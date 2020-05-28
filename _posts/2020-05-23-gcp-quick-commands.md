---

layout: post
title: GCP Quick-n-Dirty Commands
description: A list of useful gcloud and gutil commands for using Google Cloud Platforms services
published: true
categories: [Data-Science]
tags: [ds]
excerpt_separator: <!--more-->

---

A list of useful `gcloud`, `gsutil`, and `kubectl` commands for using Google Cloud Platforms. These will be continuously updated as I come across more commands. Make sure a Google Cloud project is already set up and billing is enabled.

<!--more-->

### Manage GCP configurations

* List Cloud SDK properties: `gcloud config list`
* Set a Cloud SDK property: `gcloud config set`
* Unset a Cloud SDK property: `gcloud config unset`

### Manage GCP projects

* Create new project: `gcloud projects create <project_id>`
* List accessible projects: `gcloud projects list`
* Get project metadata: `gcloud projects describe <project_id>`
* Update project name: `gcloud projects update <project_id> --name=<new-name>`
* Delete project: `gcloud projects delete <project_id>`

Additional: 
* [Creating and manging projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects)

### GCP Cloud Storage

1. Make bucket: `gsutil mb gs://<bucket-name>`
2. Move/rename objects: `gsutil mv gs://<bucket-name>/<object-name>`
3. Copy data between local file system and cloud: `gsutil cp <src-url> <dst-url>`
3. Remove object: `gsutil rm gs://<bucket-name>/<object-name>`
4. Remove bucket: `gsutil rb gs://<bucket-name>` (bucket must be empty)

Additional: 

* List buckets (with additional info): `gsutil ls <bucket-name>`

### GCP Compute Engine instance

1. Create instance: `gcloud compute instances create <instance-name>`  
2. Start instance: `gcloud compute instances start <instance-name>`  
3. Send file to instance: `gcloud compute scp --recurse ~/<local-directory> <instance-name>:~/`
4. Stop instance: `gcloud compute instances stop <instance-name>`  
5. Delete instance: `gcloud compute instances delete <instance-name>`

Additional: 

* List instances: `gcloud compute instances list`  

\*Commands can work with multiple instances by separating instance names by space

### GCP Cloud Datalab instance

*An easy-to-use interactive tool for data exploration, analysis, visualization, and machine learning via a Jupyter notebook UI. Can be used to build, test, and deploy scalable ML models.*

1. Install `datalab` component for the `gcloud` CLI: `gcloud components install datalab`
2. Create Cloud Datalab instance: `datalab create <instance-name>`
3. Open the Cloud Datalab home page in your browser: `http://localhost:8081`
4. Copying notebooks from the Cloud Datalab VM: `gcloud compute scp --recurse datalab@<instance-name>:/mnt/disks/datalab-pd/content/datalab/notebooks <local-directory-path>`
5. Delete instance 
	* Delete instance and storage disk: `datalab delete --delete-disk <instance-name>`
	* Delete the `datalab-notebooks` Cloud Source Repository, which is set up for you to store your notebooks: `gcloud source repos delete datalab-notebooks`
	* Delete the datalab-network Virtual Private Cloud (VPC) network, to which Datalab instances are connected by default: `gcloud compute networks delete datalab-network`

Additional: 

* [Datalab Quickstart](https://cloud.google.com/datalab/docs/quickstart)
* [Working with notebooks](https://cloud.google.com/datalab/docs/how-to/working-with-notebooks)