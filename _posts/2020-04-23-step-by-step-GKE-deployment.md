---
layout: post
title: Step-by-step Streamlit app deployment via GKE
description: 
published: true
excerpt_separator: <!--more-->
categories: [Data Science]
---

![pair-gke-deployment](/static/imgs/pair-gke-deployment.png "pair-gke-deployment")

Previously I introduced [Pair](http://bit.ly/pair-app), an image-based product collection recommender built using [Streamlit](www.streamlit.io) and deployed online using [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine) and [Google Cloud Platforms](https://cloud.google.com/). Recently I also deployed [COV19 Tracker](http://bit.ly/cov19-tracker), an uncluttered dashboard that visualizes the latest COVID-19 case numbers across the world and in the US. In this post I will go through the step-by-step process of how I deployed those applications from start to finish. The workflow may seem long at the first glance, but it will be much faster once you go through it once. The workflow is based on this GKE tutorial on [deploying a containerized web application](https://cloud.google.com/kubernetes-engine/docs/tutorials/hello-app).

<!--more-->

## Prerequisites

1. **Google Cloud SDK:** Before we start, you need to [install the Cloud software development kit (SDK)](https://cloud.google.com/sdk/install), which includes the `gcloud` command-line tool that provides the primary command-line interface for Google Cloud. 

2. **Kubenetes SDK:** After you install `gcloud`, you need to install the `kubectl` command-line tool, which provides the primary command-line interface for running commands against Kubernetes clusters. `kubectl` can be installed via the following command: `gcloud components install kubectl`.

3. **Docker:** You also need to [download and install Docker application](https://docs.docker.com/get-docker/). If you are new to Docker, here's a [quickstart guide](https://docs.docker.com/get-started/).

4. **GCP account:** Deployment via GCP will incurr a charge, so you need to register for an GCP account. 

## Workflow

Once you have completed the above prerequisites, you're ready to start the 6-step deployment workflow. In short, you will Dockerize your app, test your Docker image locally, then send the image to the cloud. Once that's done, you will create a container cluster, deploy your app, and expose the app to the internet.

1. **Dockerize the app:** You need to first build a Docker image (think of the recipe for a cake) of your application. See here for a [quick tutorial](https://docs.docker.com/get-started/part2/). In short, this involves
	
	1. Defining Dockerfile
	2. Building the Docker image

	**Tip:** Even before Dockerizing, create your requirements.txt and try installing all the dependencies in a clean virtual machine to see if you included all the required libraries and packages. If the app runs successfully after installation, then you can be more confident that the Docker image will be error-free. This could save time in the long run because Dockerization takes a few minutes depending on your files and dependencies, so having to re-Dockerize after fixing every dependency error could be time-consuming.

2. **Test the container locally:** Test run the image as a container (think of the cake made from the recipe) by 

	`docker run --rm -p 8501:8501 gcr.io/{$PROJECT_ID}/*your-app-name*:v1`

	Then point your internet browser to `localhost:8501` to see the app. If it shows up as you expected, then you know your application is ready for the big time.

	**Note:**
	* `-p` -- or the `--publish` flag -- asks Docker to forward incoming traffic on the host’s port to the container’s port (the specific port used by Streamlit is 8501). Containers have their own private set of ports, so if you want to reach one from the network, you have to forward traffic to it in this way. Otherwise, firewall rules will prevent all network traffic from reaching your container, as a default security posture. 
	* The `gcr.io` prefix refers to Container Registry, where the image will be hosted.
	* `{$PROJECT_ID}` is your GCP project ID, which you can find in the [GCP console](https://console.cloud.google.com) 
	* `:v1` keeps track of the version of your app
	

3. **Push image to Google Container Registry (GCR):** Send the image up to the cloud to prepare for deployment.

	`docker push gcr.io/{$PROJECT_ID}/*your-app-name*:v1`

4. **Create a container cluster:** Create a [cluster](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture) to run the container image. It basically means intiailizing a group of computing resources that will run the app. You need to first set default Google Cloud options that tells gcloud where to find resources to set up the cluster

	`gcloud config set project $PROJECT_ID`  
	`gcloud config set compute/zone $COMPUTE_ZONE`

	Then create the cluster (in this example with 2 nodes) by 

	`gcloud container clusters create *your-cluster-name* --num-nodes=2`

	**Note:** If you are using an existing Google Kubernetes Engine cluster or if you have created a cluster through Google Cloud Console, you need to run the following command to retrieve cluster credentials and configure kubectl command-line tool with them:

	`gcloud container clusters get-credentials *your-cluster-name*`

	If you have already created a cluster with the gcloud container clusters create command listed above, this step is not necessary.

5. **Deploy your application:** Make multiple copies of your app via Kubernetes clusters management system.

	```
	kubectl create deployment *your-web-deployment-name* --image=gcr.io/{$PROJECT_ID}/*your-app-name*:v1
	```

	Kubernetes represents applications as [Pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/), which are units that represent a container (or group of tightly-coupled containers). The Pod is the smallest deployable unit in Kubernetes. In this tutorial, each Pod contains only the Docker container of your app.

6. **Expose your application to the internet:** Assign external IP addresses for your app so it is accessible from the internet.

	`kubectl expose deployment *your-web-deployment-name* --type=LoadBalancer --port 80 --target-port 8501`

	This command creates a [Service](https://kubernetes.io/docs/user-guide/services/) resource, which provides networking and IP support to your application's Pods. GKE creates an external IP and a Load Balancer for your application. After a minute or so, an `EXTERNAL-IP` will be assigned to your app. You can find it via

	`kubectl get service` 

	which will show something like this:

	```
	NAME  		    	     CLUSTER-IP    EXTERNAL-IP  PORT(S)       AGE
	*your-web-deployment-name*  10.3.251.122  203.0.113.0  80:30877/TCP  3d
	```

	Point your browser to this URL (such as `http://203.0.113.0`) and you should be able to access the app! If it shows up and works as you expected, then you're done. Congratulations!

7. **Iterate on your app:** At this point your app is live on the internet, but depending on incoming traffic flow or feature suggestions by your users, you maybe want to make changes to your deployment infrastructure or your app. You can continue to adjust the number of nodes you want to use for the cluster with 

	`kubectl scale deployment *your-web-deployment-name* --replicas=*num-of-nodes*`.

	Another way to change the the number of nodes is via `gcloud` (I'm not sure how they differ). First get the name of your container cluster,

	`gcloud container clusters list`,

	then 

	`gcloud container clusters resize *container-cluster-name* --num-nodes *num-of-nodes*`.

	You can continue to iterate on newer versions of your app locally. When you are ready to release a newn version of your app, go through steps 1-3 again (remember to increment the version when creating new Docker images). Once the image is in GCR, you can update the deployment via

	```
	kubectl set image *your-web-deployment-name* *your-app-name*=gcr.io/${PROJECT_ID}/*your-app-name*:v2
	```

## Conclusion

In this tutorial I went through my step-by-step workflow for deploying my Streamlit applications onto the internet using GCP and GKE. Keep in mind that GCP offers a [multitude of cloud services](https://cloud.google.com/docs/overview/cloud-platform-services), and here I've only touched on container-based computing with GKE. Anyhow, hopefully this tutorial can help you get your own application up and running on the cloud ASAP! Feel free to reach out to me if you find and errors or have any suggestions. Happy deployment!

