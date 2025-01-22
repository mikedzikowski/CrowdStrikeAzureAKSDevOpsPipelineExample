# CrowdStrike Azure Kubernetes Service Example Pipeline

This repo contains an example Azure DevOps pipeline that deploys the CrowdStrike sensor, Kubernetes Admission Controller and IAR (Image Assesment at Runtime) tools on an exisiting Azure Kubernetes Service cluster.

The pipeline uses Az CLI and Helm charts to deploy the utilities. For more information on the CrowdStrike helm charts read the documentation here:

[Falcon Helm](https://github.com/CrowdStrike/falcon-helm/tree/main)

The required zAzure DevOps service connections, configuration and AKS setup are not covered in this brief demo example.



