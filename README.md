# CrowdStrike Azure Kubernetes Service Example Pipeline

This repo contains an example Azure DevOps pipeline that deploys the CrowdStrike sensor, Kubernetes Admission Controller and IAR (Image Assesment at Runtime) tools on an exisiting Azure Kubernetes Service cluster.

The pipeline uses Az CLI and Helm charts to deploy the utilities. For more information on the CrowdStrike helm charts read the documentation here:

[Falcon Helm](https://github.com/CrowdStrike/falcon-helm/tree/main)

The required Azure DevOps service connections, configuration and AKS setup are not covered in this brief demo example.

# Pipeline Variables Reference Guide

This document provides details about the variables used in the CrowdStrike Falcon deployment pipeline.

## CrowdStrike Falcon Credentials

| Variable | Description |
|----------|-------------|
| `fcsClientId` | The CrowdStrike Falcon API Client ID used to authenticate with the CrowdStrike API. Generate this in the CrowdStrike console under API Clients & Keys. |
| `fscSecret` | The CrowdStrike Falcon API Client Secret paired with the Client ID for authentication. Keep this value secure. |
| `fcsCID` | Your unique CrowdStrike Customer ID (CID) that identifies your Falcon environment. Format typically includes hyphens and alphanumeric characters. |

## Azure Configuration

| Variable | Description |
|----------|-------------|
| `azureSubscription` | The service connection for DevOps The Azure Subscription ID where resources will be deployed. This is a GUID that identifies your Azure subscription. |
| `clusterName` | The name of the Azure Kubernetes Service (AKS) cluster to be created or used. Default: 'aks-cluster' |
| `clusterResourceGroup` | The Azure Resource Group where the AKS cluster will be deployed. Default: 'rg-example-eu1' |
| `APP_ID` | The Azure Application (Service Principal) ID used for authentication with Azure services. |
| `CLIENT_SECRET` | The secret/password for the Azure Service Principal. Keep this value secure. |
| `TENANT_ID` | The Azure Active Directory tenant ID associated with your Azure subscription. |
| `SUBSCRIPTION_ID` | Same as azureSubscription, the Azure Subscription ID where resources will be deployed. |

## Registry Configurations

| Variable | Description |
|----------|-------------|
| `sensorRegistry` | The CrowdStrike container registry path for the Falcon Sensor. Default: 'registry.crowdstrike.com/falcon-sensor/us-1/release/falcon-sensor' |
| `kacRegistry` | The CrowdStrike container registry path for the Kubernetes Admission Controller. Default: 'registry.crowdstrike.com/falcon-kac/us-1/release/falcon-kac' |
| `iarRegistry` | The CrowdStrike container registry path for the Image Analyzer. Default: 'registry.crowdstrike.com/falcon-imageanalyzer/us-1/release/falcon-imageanalyzer' |
| `acrRegistry` | Your Azure Container Registry URL where images will be stored. Default: 'contoso.azurecr.io' |

## Docker Authentication

| Variable | Description |
|----------|-------------|
| `DOCKER_USER` | Username for Docker registry authentication. |
| `DOCKER_PASSWORD` | Password for Docker registry authentication. Keep this value secure. |
| `DOCKER_EMAIL` | Email address associated with the Docker registry account. |

## Notes

- All sensitive values should be stored as secure pipeline variables or in a secure vault.
- The registry paths may need to be updated based on your CrowdStrike region.
- The Azure resource names should be changed to match your environment naming conventions.
- Ensure the Azure Service Principal has appropriate permissions to create and manage AKS clusters and container registries
