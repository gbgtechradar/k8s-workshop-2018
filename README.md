# Introduction to Kubernetes - Workshop

The purpose of this workshop is to let people getting started with Kubernetes and to be able to continue playing around after the workshop ends. As primary tool we plan to use minikube because that's a kube environment that you can run locally.

## Preparations

The workshop has limited time so to get the most out of it we recommend you to install the tools needed. You will need both [Docker CE](https://www.docker.com/) and [Minikube](https://github.com/kubernetes/minikube) installed.

Minikube: https://kubernetes.io/docs/tasks/tools/install-minikube/<br/>
Docker: https://docs.docker.com/install/<br/>
Direct link for Mac: https://docs.docker.com/docker-for-mac/install/<br/>
Direct link for Ubuntu: https://docs.docker.com/install/linux/docker-ce/ubuntu/

Most of the tutorials can be run online using [Katacoda](https://www.katacoda.com/courses/kubernetes/playground) or [Play with Kubernetes](https://labs.play-with-k8s.com). It's free to create account. 

### Katacode

The Katacoda has a intuitive GUI that helps you with everything. Really easy to go thru the tutorials, it feels very much like a demo. 

### Play with Kubernetes

Play with Kubernetes is much more hands on. You have to run commands to setup the cluster (easy instructions on the site). On the other hand this is a more real experience. You can/have to create several nodes. You will have your session for 4 hours.

**Basic steps**

1. Create instance and run kubeadm command for create master node and then create a network.
2. Create one or more instance and run join command that was shown after the master node was created.
3. Use the master node to run all your kubectl command. 

## Workshop

### Hello Minikube

This tutorial goes thru the how to install Minikube (on Mac) and to run your first application on Kubernetes. It's a simple "Hello World"-web server and takes you thru all steps from writing the web application with nodejs, packaging the application in a container and deploy it to Kubernetes. This is a good start if you not yet have minikube installed or not worked with containers before.

Link: [Hello Minikube](https://kubernetes.io/docs/tutorials/stateless-application/hello-minikube/)

### Kubernetes 101

Here you can see how you write definition specification for resources that you create in Kubernetes. Everything in Kubernetes are specified as resources and they are written as yaml or json-files. Most examples use to show yaml-files because they have a cleaner look. You will learn what a pod is and how it is specified, how persistence storage is done and how to run multiple containers as a group. **Note!** The last example doesn't contains a working example, but try it anyway and see how Kubernetes will handle it. _Hint_: `kubectl describe pod www`

Link: [Kubernetes 101](https://kubernetes.io/docs/user-guide/walkthrough/)

### Kubernetes 201

201 will give you more insights in the power of Kubernetes. You will see how labels can be used for grouping pods to services and how a full deployment is specified. Finally you will see how the build in pod monitoring functionality works in Kubernetes.

Link: [Kubernetes 201](https://kubernetes.io/docs/user-guide/walkthrough/k8s201/)

### Guestbook

The Guestbook example shows a complete application deployment in Kubernetes. It includes a web frontend and a redis database as backend. The deployment is a full redundant configuration with a scalable frontend. Running this example on "Play with Kubernetes" can be extra interesting to see how the pods are distributed between serveral nodes.

Link: [Guestbook](https://kubernetes.io/docs/tutorials/stateless-application/guestbook/)
