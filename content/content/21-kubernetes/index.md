---
title: "Kubernetes"
lastmod: 2022-10-06T00:00:00+08:00
draft: false
tags: [kubernetes]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

[Notes](../../notes) / [Kubernetes](./)

## Overview

* A container orchestrator that makes sure that each container is where it's supposed to be and that the containers can communicate
* k8s --> acronym for the 8 letters between the k and the s in kubernetes
* When working with Kubernetes, you could also be working with [Docker](./docker.md) for containers
* Kubernetes manages running multiple containers on a single machine
* Kubectl is the Kubernetes CLI
* Kubernetes configuration is done using `.yaml` files
* Kubernetes provides you with the following out of the box:
  * Service discovery and load balancing
  * Storage orchestration
  * Automated rollouts and rollbacks
  * Automatic bin packing: fitting containers onto your nodes to make the best use of resources
  * Self healing: You provide a health-check endpoint, Kubernetes checks it and replaces containers that don't respond to it as expected
  * Secret configuration and management: Lets you deploy and update secrets and app configuration without rebuilding your container images

## Learning Resources

### Articles

* [ ] [Kubernetes 101](https://medium.com/google-cloud/kubernetes-101-pods-nodes-containers-and-clusters-c1509e409e16), [110](https://medium.com/google-cloud/kubernetes-110-your-first-deployment-bf123c1d3f8), [120](https://medium.com/google-cloud/kubernetes-120-networking-basics-3b903f13093a)
* [ ] [Kubernetes Overview Documentation](https://kubernetes.io/docs/concepts/overview/)
* [ ] [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
* [ ] Kubernetes from basics to autoscaling ([4 parts](https://softchris.github.io/pages/kubernetes-one.html))
* [ ] Read the [core concepts](https://kubernetes.io/docs/concepts/)
* [ ] [Operating k8s](https://stripe.com/blog/operating-kubernetes) and what could break (also in [video](https://www.youtube.com/watch?v=obB2IvCv-K0) form)
* [ ] [Azure Kubernetes Service learning and training](https://azure.microsoft.com/en-us/resources/kubernetes-learning-and-training/#overview)
* [ ] [Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) is the standard for a bottom-up understanding of k8s
* [ ] AKS is Azure's managed Kubernetes configuration, which makes additions and constraints to Kubernetes. The [AKS Baseline](https://github.com/mspnp/aks-baseline) is a set of recommendations and[reference implementations](https://github.com/mspnp/aks-baseline) for using AKS effectively within these constraints.
* [ ] [istio.io](https://istio.io/) is a good starting place for understanding Istio, and has all the official documentation.

### Videos

* [ ] [Video: What is Kubernetes](https://www.youtube.com/watch?v=cC46cg5FFAM)
* [ ] [Video: Kubernetes and Docker](https://www.youtube.com/watch?v=PfRWP60qxPM)
* [ ] HoneyPot on Kubernetes Documentary
* [ ] Watch the videos on <https://kustomize.io/>.
* [ ] Video of a talk on [Kustomize](https://www.youtube.com/watch?v=ahMIBxufNR0) from KubeCon 2018. A nice introduction to Kustomize and understanding what problems the tool is attempting to solve.

### Books

* [ ] [Istio in Action](https://www.manning.com/books/istio-in-action) is a more in-depth book about the ins and outs of using Istio
