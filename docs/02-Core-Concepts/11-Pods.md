# Pods
  - Take me to [Video Tutorial](https://kodekloud.com/topic/pods-2/)
  
In this section, we will take a look at PODS.
- POD introduction
- How to deploy pod?

#### Kubernetes doesn't deploy containers directly on the worker node.

  ![pod](../../images/pod.PNG)
  
#### Here is a single node kubernetes cluster with single instance of your application running in a single docker container encapsulated in the pod.

![pod1](../../images/pod1.PNG)

#### Pod will have a one-to-one relationship with containers running your application.

  ![pod2](../../images/pod2.PNG)

#### To scale up you create a new Pod and to scale down you delete existing Pod. You do not add additional containers to an existing Pod to scale your application.
  
## Multi-Container PODs
- A single pod can have multiple containers except for the fact that they are usually not multiple containers of the **`same kind`**.
  
  ![pod3](../../images/pod3.PNG)
  
## Docker Example (Docker Link)
  
  ![pod4](../../images/pod4.PNG)

#### In the Docker Example scenario, we need to maintain a map of what app and helper containers are connected to each other. We would need to establish network connectivity between these containers ourselves using links and custom networks. We would need to create shareable volumes and share it among the containers. We would need to maintain a map of that as well, and most importantly, we would need to monitor the state of the application container and when it dies, manually kill the helper container as well as it's no longer required. When a new container is deployed, we would need to deploy the new helper container as well. With pods, Kubernetes does all of this for us automatically. We just need to define what containers a pod consists of and the containers in a pod by default will have access to the same storage, the same network namespace and same fit as in they will be created together and destroyed together. Even if our application didn't happen to be so complex and we could live with a single container, Kubernetes still requires you to create pods, but this is good in the long run as your application is now equipped for architectural changes and scale in the future.
  
## How to deploy pods?
Lets now take a look to create a nginx pod using **`kubectl`**.

- To deploy a docker container by creating a POD.
  ```
  $ kubectl run nginx --image nginx
  ```

- To get the list of pods
  ```
  $ kubectl get pods
  ```

 ![kubectl](../../images/kubectl.PNG)

K8s Reference Docs:
- https://kubernetes.io/docs/concepts/workloads/pods/pod/
- https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/
- https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/


