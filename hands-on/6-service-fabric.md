# 6 - Service fabric

Containers can live and be served through Service fabric and be managed and scaled using Azure Service fabric and it's capabilities. You can also deploy existing web-apis, wcf, console apps++ in Service fabric and leverage it's capabilities for resiliance and scalability.

The following will give you a little hands-on in utilizing service fabric for deploying , scaling and managing containers. 

## Getting started
 
   - Install Service Fabric SDK on your machine (Web installer)
   - Set up your local dev machine to have 5 nodes
   - Make sure your cluster is running  
        - http://localhost:19080/Explorer/index.html#/
   
    
## Your first project
    - Start VS 2017
    - Create a new Service fabric application
    - Check out the different options you have available
        - You can adopt/deploy most projects into your SF cluster
    - Create two simple applications
        - Test out the .NET Core application
        - Test out the guest executable
    - Explore the deployment script generated for you
    - Explore the service manifests and the application manifests
        - How are they put up?
        - How are endpoints exposed?
        - How are the services running up?
    - Containers is not available OOTB running on Win10 (needs to run on Server2016)
        - Set up cluster (local) to run win server2016
        
    
# Explore the cluster and some options
    - Deploy a few applications
    - Explore variables and sharing                
    - Discover service discovery
    - You can use service fabric and discovery to request a service!
    - Force shut down a node
    - See that the node comes up again

# Install service fabric on server 2016 (hyper-v)
    - Explore the container options
    - Connect your local dev machine to your server cluster
    - Deploy services to you windows server 2016 cluster


# Some reading material
 - <a hreF="https://github.com/Microsoft/azure-docs/blob/master/articles/service-fabric/service-fabric-deploy-container-linux.md"> Some resources </A>
 - <a hreF="https://blogs.msdn.microsoft.com/azureservicefabric/2016/04/25/orchestrating-containers-with-service-fabric/">Orchestration containers</a>
