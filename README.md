# istio-project

Service Mesh study. Tutorial of the Course Uncomplicating Istio of the LinuxTIPS.

# Summary

**[What is Service Mesh?](#what-is-service-mesh)**<br>
**[Creating a K8S Cluster with Kind](#creating-a-k8s-cluster-with-kind)**<br>
    - [Install Kind (Windows)](#install-kind-windows)<br>
    - [Creating a Cluster](#creating-a-cluster)<br>
**[Installing-Istio](#installing-istio)**<br>

## What is Service Mesh?

When we have a MicroService archtecture in our environment and this environment is so much big, we have problems with observability and collection of metrics of the each service. It's in this point that the Service Mesh comes in as a Solution, with observability and control of traffic in each requisition of the services.

The Istio Service Mesh is the more famous in K8S Cluster and this tool have too much features that i will explore in this repository. In addition the Istio Service Mesh also configures Security tools and metrics of requisitions that we can track back (trace) and verify the return of each requisition.

## Creating a K8S Cluster with **Kind**

This is a test K8S Cluster created with Docker "Nodes". Used to test applications and features locally. It's a simple tool to study and make tutorials.

### Install Kind (Windows)

See the official documentation of (installation)[https://kind.sigs.k8s.io/docs/user/quick-start/#installation]. 

```
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.17.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe
```

### Creating a Cluster

```
kind create cluster --config=cluster.yaml
```

## Installing Istio