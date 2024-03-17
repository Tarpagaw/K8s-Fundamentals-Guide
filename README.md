
### Kubernetes Fundamentals: Understanding pods and nodes.





## Introduction

Kubernetes, often abbreviated as k8s, has emerged as the de facto system for orchestrating containerized applications. Within this ecosystem, the concepts of "pods" and "nodes" are fundamental to understanding how Kubernetes manages and schedules applications. A pod is the smallest deployable unit created and managed by Kubernetes, while a node is the physical or virtual machine that hosts these pods. The purpose of this article is to guide you through the basics of pods and nodes, along with a simple example of how to deploy a pod using k8s commands.


## Pods 
A pod is essentially a group of one or more containers with shared storage/network resources and a specification for how to run the containers. Containers in the same pod have the same IP address and port space, and can find each other via localhost. They also have access to shared volumes, allowing them to communicate through file sharing.

Pods are ephemeral in nature. They aren't designed to last forever; when a pod dies, it is not resurrected. Instead, Kubernetes uses controllers like Deployments to maintain the desired state, such as keeping a certain number of identical pods running.

## Nodes 
Nodes are the workhorses of a Kubernetes cluster. Each node can be a virtual or physical machine, depending on the cluster. Every node is managed by the master components and includes the services necessary to run pods, managed by the Kubernetes runtime environment, such as Docker.

A Kubernetes node has several necessary components, such as kubelet, which manages the node's communication with the Kubernetes master. The kube-proxy maintains network rules that allow network communication to your pods from inside or outside the cluster.

## Deploying a Pod
Deploying a pod in Kubernetes is done through a command-line interface tool called kubectl. Here's a basic example of a pod deployment:

First, you define your pod in a YAML file (pod-definition.yml):

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-sample-pod
spec:
  containers:
  - name: my-container
    image: nginx
```

This YAML snippet defines a simple pod named my-sample-pod with a single container running the nginx image.

To deploy this pod into your cluster, you would use the following k8s command:

`kubectl apply -f pod-definition.yml`


This command tells Kubernetes to create the objects described in the pod-definition.yml file, in this case, a pod.

After running the command, you can check the status of your pod with:

`kubectl get pods`

Once the pod is running, you should see the my-sample-pod listed as available.

## Conclusion
Understanding pods and nodes is crucial for anyone looking to work with Kubernetes. Pods are where your application components run, and nodes are where these pods are scheduled and maintained. The beauty of Kubernetes is its ability to manage these pods across a cluster of nodes, handling failures and scaling with ease. By deploying a simple pod with kubectl, users can take their first step into Kubernetes' orchestration and witness the power of container management.

## References

      - Kubernetes.io: Viewing Pods and Nodes

        Link: https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/


        