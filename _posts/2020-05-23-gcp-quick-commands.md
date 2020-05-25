---

layout: post
title: GCP Quick-n-Dirty Commands
description: A list of useful gcloud and gutil commands for using Google Cloud Platforms services
published: true
categories: [Data-Science]
tags: [ds]
excerpt_separator: <!--more-->

---

A list of useful `gcloud` and `gutil` commands for using Google Cloud Platforms services. These will be continuously updated as I come across more commands.

<!--more-->

### GCP Compute Engine instance

Create instance: `gcloud compute instances create INSTANCE_NAME`  
Start instance: `gcloud compute instances start INSTANCE_NAME`  
List instances: `gcloud compute instances list`  
Stop instance: `gcloud compute instances stop INSTANCE_NAME`  
Delete instance: `gcloud compute instances delete INSTANCE_NAME`

\*Commands can work with multiple instances by separating instance names by space
