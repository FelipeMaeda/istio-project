# istio-project

Service Mesh study. Tutorial of the Course Uncomplicating Istio of the LinuxTIPS.

# Summary

* **[What is Service Mesh?](#what-is-service-mesh)**<br>
* **[Creating a K8S Cluster with Kind](#creating-a-k8s-cluster-with-kind)**<br>
   * [Clone this repo](#clone-this-repo)<br>
   * [Install Kind (Windows)](#install-kind-windows)<br>
   * [Creating a Cluster](#creating-a-cluster)<br>
* **[Installing-Istio](#installing-istio)**<br>

## What is Service Mesh?

When we have a MicroService archtecture in our environment and this environment is so much big, we have problems with observability and collection of metrics of the each service. It's in this point that the Service Mesh comes in as a Solution, with observability and control of traffic in each requisition of the services.

The Istio Service Mesh is the more famous in K8S Cluster and this tool have too much features that i will explore in this repository. In addition the Istio Service Mesh also configures Security tools and metrics of requisitions that we can track back (trace) and verify the return of each requisition.

## Creating a K8S Cluster with **Kind**

This is a test K8S Cluster created with Docker "Nodes". Used to test applications and features locally. It's a simple tool to study and make tutorials.

### Clone this repo

Before you start with the creation of the Cluster, clone this repository.

```
git clone https://github.com/FelipeMaeda/istio-project.git
cd istio-project
```

### Install Kind (Windows)

See the official documentation of [**installation**](https://kind.sigs.k8s.io/docs/user/quick-start/#installation) for **Linux** and **MacOS** computers. 

```
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.17.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe .\kind.exe
```

### Creating a Cluster

To manage the Cluster it's be necessary that you have [**kubectl installed**](https://kubernetes.io/docs/tasks/tools/#kubectl) in your computer.

```
kind.exe create cluster --config=cluster.yaml

# Verify the kubeconfig file in Windows
type ~/.kube/config

# Verify the kubeconfig file in Linux or MacOS
cat ~/.kube/config
```

## Installing Istio

To install Istio Service Mesh in your computer, you need to get the latest version compatible with your OS in the oficial [**repository link**](https://github.com/istio/istio/releases). The Istio Service Mesh is Open Source, for this reason the repository have the code of this tool.

In your compressed file of the Istio, you have a "bin" folder that contain you **istioctl** binary file. This is the principal tool to execute the installation of the Istio in your K8S Cluster based in the cluster configured in your **kubeconfig** file (if you have more than one cluster, you need to specify them in the Command Line).

```

```