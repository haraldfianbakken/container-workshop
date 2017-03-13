# 7 - Azure deployments

There's quite a few ways of building, deploying, running and managing containers in Azure today. 
These handson exercises will give you some experience in managing and setting up some possible scenarios.

## Login to portal.azure.com & create a resource group
 - Create a resource group called containerDemo2017
 - This will be your group for deployments - Remember to clean it up when done with the handson
 

## Sign up to hub.docker.com
 - Create an account at docker.com. 
 - Create a private repository for this demo

## Building your container
 - Explore the docker local commands
     - docker --help
     - docker build --help
 - Build an image off a base image
    - List your local images
 - Push your image to the private docker repository
    - docker push --help
 
## Deploy docker container to Azure app service
 - Log in to Azure 
 - Create an App service (on Linux)
 - Configure the docker option
 - Enter your credentials
 - Deploy your container and verify that you can run and access your container
 - Configure automatic deployment for new versions

## Create a free VSTS account and setup deployment
 - Create a free VSTS account
 - Create a new project for building docker containers
 - Clone the empty repository
 - Create a simple docker project or replicate one of your existing ones
 - Push your code
 - Create a build definition for building your docker container
 - Create a release definition for your build
 - Setup a continous deployment pipeline for automating deployment of the docker container

<a href="https://blogs.msdn.microsoft.com/jcorioland/2016/08/19/build-push-and-run-docker-images-with-visual-studio-team-services/"> Some good documentation can be found here </a>

## Create a private container registry
 - Explore the Azure Container registry
 - Create a container registry
 - Select your resource group
 - Enable the admin user and create yourself a user
 - Create a new storage account for the storage needed by the container registry

 Now, push your image to your new private docker registry and make sure you can find it 

Optional: 
 - Try: reconfigure VSTS to use your private container registry instead of docker

## Getting to know container services
 - Create a container service in portal.azure.com 
 - Try recreating / or running your previously created container in the container services using kubernetes or one of the alternatives
 

## Getting to know Azure service fabric 
Optional if time. You will spend a lot of time configuring and waiting for Azure to provision the hardware needed. 
You could easily work two on this exercise as you'll spend most of your time waiting.
 
 - Build your Azure service fabric cluster
     - Documentation can be found here : <a href="https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-cluster-creation-via-arm">Create service fabric</a>
 - When service fabric is provisioned and up running, deploy your docker containers to the environment. 
 - Try scaling up and down the services

## Clean up and delete provisioned resources
 When you're done, make sure you delete your AzureDemo2017 resource group. Else the costs will run and eat your credits!