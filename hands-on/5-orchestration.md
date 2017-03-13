# 5 - Orchestration

When working with large deployments and scalability, one should know a little about the tooling and framework support. 

These exercises will give you some idea on how to do and work with simple orchestration and scaling in the docker world. 

NB: For this exercise you will have to have installed Hyper-V


## Getting started
  - Install Minikube into c:\kube\
  - Set the path to c:\kube
  - Make sure you can run minikube.exe 
  - verify the version
  - Check $home\.minikube (or %HOMEPATH%\.minikube)
  - Explore the help utils "minikube.exe --help"


## Starting your cluster
   - Explore the help for starting 
       - minikube.exe start --help
   - Start the local cluster by doing the following
``` 
.\minikube.exe start --kubernetes-version="v1.4.0" 
                             --vm-driver="virtualbox" 
                             --show-libmachine-logs --alsologtostderr
```

This will do the following

  1. Generates the certificates, provisions a local docker host inside hyper-v
  2. The host is porivisined with boot2Docker
  3. Fixes IPs and the stuff
  4. Shows a message that all went well.

  Check the status of kubernetes:

```minikube.exe -status ```


Get cluster information

```kubectl.exe -cluster-info ```

## Show the dashboard and the nodes attached

```minikube.exe dashboard  ```

If you just want the URL get it using :

```minikube.exe dashboard --url=true ```


If you rather use the commandline to show the nodes

```kubectl.exe get nodes```

## Run a container in kubernetes

Get a default image up running

```
.\kubectl.exe run hello-nginx --image=nginx --port=80
deployment "hello-nginx" created
```

Verify that the status is OK or ContainerCreating


## Expose deployment as a scalable service

```
.\kubectl.exe expose deployment hello-nginx --type=NodePort
service "hello-nginx" exposed

# Verify that it is running successfully
\kubectl.exe get services

# Get the service url for this service
.\minikube.exe service --url=true hello-nginx

# Open the service in your browser
.\minikube.exe service hello-nginx
```

## View logs
  - Navigate to the kubernetes dashboard
  - Find your newly exposed service
  - Click the particular pod and view logs

From the commandline
```
.\kubectl logs <podname>
```

## Scaling

Now the fun will start. Scale your instance to 4 instances

```
\kubectl scale --replicas=3 deployment/hello-nginx
deployment "hello-nginx" scaled 

# Get the status
.\kubectl.exe get deployment
```

## Deployments by configuration
Kubernetes accepts deployments from configuration using yaml. If you'd like to test this out, you can read the documentation here <a href="https://kubernetes.io/docs/tutorials/stateless-application/run-stateless-application-deployment/#updating-the-deployment">stateless deployments</a>

## Deploy your own images

Now you can test and run the previously created containers.

  - Deploy your API , Web and own Nginx containers from your previous examples
  - Configure the containers in kubernetes
     - See if you can build the configuration (like docker compose) rather then configuring them individually
     (e.g. compose2kube and inspect the output yaml files )
  - Scale them to e.g. 3 instances


## Autoscale (horizontal pod scaling)

Try configuring your API that processes images for autoscaling when your API gets to busy (e.g. over 65% cpu load).

<a href="https://kubernetes.io/docs/user-guide/horizontal-pod-autoscaling/  ">Read documentation here</a>

## Running windows containers in Kubernetes
If you'd like you can try running the windows containers from previous example in Kubernetes. 

For more info <a href="https://kubernetes.io/docs/getting-started-guides/windows/">read documentation here</a>


## Alternative tool to Kubernetes (Docker Swarm)
You can choose to do the same exercises using docker swarm (docker native) support. For more info and comparission, these links provide good insights: 
- <a href="https://technologyconversations.com/2015/11/04/docker-clustering-tools
-compared-kubernetes-vs-docker-swarm/">Kubernetes vs docker swarm</a>
- <a href="https://www.upcloud.com/blog/docker-swarm-vs-kubernetes/">Docker swarm vs kubernetes</a>