# Istio

Service Mesh study. Tutorial of the Course Uncomplicating Istio of the LinuxTIPS.

# Summary

* **[What is Service Mesh?](#what-is-service-mesh)**<br>
* **[Preparing the Environment](#preparing-the-environment)**<br>
* **[Creating a K8S Cluster with Kind](#creating-a-k8s-cluster-with-kind)**<br>
   * [Clone this repo](#clone-this-repo)<br>
   * [Install Kind (Windows)](#install-kind-windows)<br>
   * [Creating a Cluster](#creating-a-cluster)<br>
* **[Installing-Istio](#installing-istio)**<br>
* **[Creating your Sample with Helm](#creating-your-sample-with-helm)**<br>
   * [Installing Helm](#installing-helm)<br>


## What is Service Mesh?

When we have a MicroService architecture in our environment and this environment is so much big, we have problems with observability and collection of metrics of the each service. It's in this point that the Service Mesh comes in as a Solution, with observability and control of traffic in each requisition of the services.

The Istio Service Mesh is the more famous in K8S Cluster and this tool have too much features that i will explore in this repository. In addition the Istio Service Mesh also configures Security tools and metrics of requisitions that we can track back (trace) and verify the return of each requisition.

## Preparing the Environment

To study Istio, it be necessary create a Cluster K8S and Install the tools necessary to execute commands and resources of the Istio.

## Creating a K8S Cluster with **Kind**

This is a test K8S Cluster created with Docker "Nodes". Used to test applications and features locally. It's a simple tool to study and make tutorials.

### Clone this repo

Before you start with the creation of the Cluster, clone this repository.

```
git clone https://github.com/FelipeMaeda/istio-project.git
cd istio-project
```

### Install Kind (Windows)

See the [**official documentation of installation**](https://kind.sigs.k8s.io/docs/user/quick-start/#installation) for **Linux** and **MacOS** computers. 

```
curl -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.17.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe .\kind.exe
```

### Creating a Cluster

To manage the Cluster it's be necessary that you have [**kubectl installed**](https://kubernetes.io/docs/tasks/tools/#kubectl) in your computer.

```
kind create cluster --config=cluster.yaml

type ~/.kube/config

cat ~/.kube/config
```

## Installing Istio

To install Istio Service Mesh in your computer, you need to get the latest version compatible with your OS in the [**official repository link**](https://github.com/istio/istio/releases). The Istio Service Mesh is Open Source, for this reason the repository have the code of this tool.

In your compressed file of the Istio, you have a "bin" folder that contain you **istioctl** binary file. This is the principal tool to execute the installation of the Istio in your K8S Cluster based in the cluster configured in your **kubeconfig** file (if you have more than one cluster, you need to specify them in the Command Line).

```
istioctl install --set profile=demo -y
istioctl proxy-status
```

## Creating namespaces and enable Istio Sidecar Injection

```
kubectl create namespace strigus
kubectl create namespace giropops
kubectl create namespace girus

# Enable only 2 namespaces to realize tests of communication
kubectl label namespace strigus istio-injection=enabled --overwrite
kubectl label namespace giropops istio-injection=enabled --overwrite
```

## Creating a httpbin services

```
kubectl apply -f .\istio\samples\httpbin\httpbin.yaml -n strigus
kubectl apply -f .\istio\samples\httpbin\httpbin.yaml -n giropops
kubectl apply -f .\istio\samples\httpbin\httpbin.yaml -n girus
```

## Install Curl in the Pods

```
kubectl.exe exec -ti -n strigus POD_NAME -- apt-get update && apt-get install curl -y
kubectl.exe exec -ti -n giropops POD_NAME -- apt-get update && apt-get install curl -y
kubectl.exe exec -ti -n girus POD_NAME -- apt-get update && apt-get install curl -y
```

## Testing Service Communication

















# After Examples

## Creating your Sample with Helm

### Installing Helm

Access the [official documentation about Helm](https://helm.sh/docs/intro/install/#from-canary-builds) and verify the Download and Installation of the Binary File.

### Creating the Helm Sample

```
helm create nginx_sample
```
