# Deploy to Satellite

## Introduction 

Secure app toolchain provides an option to deploy your application on [IBM Cloud Satellite](https://www.ibm.com/cloud/satellite). 

## Prerequisite 

* This toolchain uses [Satellite Config](https://cloud.ibm.com/docs/satellite?topic=satellite-cluster-config) for deploying an application to a group of clusters. 
* This toolchain assumes that you have [Satellite cluster group](https://cloud.ibm.com/docs/satellite?topic=satellite-setup-clusters-satconfig) with required clusters. 
* This toolchain supports a Satellite Cluster Group that contains only one type of cluster(either IBM Kubernetes Cluster or RedHat OpenShift).

## Deployment Strategy

A [Rolling](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/) strategy will be used for deploying changes to the satellite environment.

```
1. Update the deployment file with the application image name obtained from the inventory repo.
2. Update the deployment file with default ingress.
3. Check if the satellite cluster group has a cluster of type OpenShift, if true then update the deployment file with a default route.
4. Check if the satellite cluster group does not contain a mix of IKS and OpenShift clusters. If so, then output an error.
5. Prepare the Satellite Config for kubernetes namespace and create the satellite subcription.
6. Prepare the Satellite Config for kubernetes service account and create the satellite subcription.
7. Prepare the Satellite Config for kubernetes application deployment and create the satellite subcription.
8. Check the application rollout status.
```






