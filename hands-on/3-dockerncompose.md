# 3 - Docker and docker compose

You will now get some hands-on with using images from the docker-hub and built incremental images. You will also use docker compose to create more complex scenarios for spinning up dependencies in a docker environment.

For the simplicity we will base our images on public images from the public repos on <a href="https://hub.docker.com">https://hub.docker.com</a>.

For inspiration for images, check out : <a href="https://hub.docker.com/explore/">Explore repositories</a>

## Build your first container (database)
 - Find a database (base) image of your choice (postgres,mssql,mysql)
 - Create a simple database schema 
     - One table : blobid, blobname, isProcessed (bool), result (text/json)
 - Extend your container with DB-initializiation
     - Create a database and a user with admin rights to that DB
     - Execute *.sql scripts for initializiation    
 
## Build your second container
 - Find a base image of your choice
 - Extend the image with a file storage from your host , this will be used for storing blobs
 - Create an API for posting blobs (nodejs/aspnetcore)
 - When receiving the blob, put a record into the database and the blob in the storage.
 

## Create your docker compose
 - Create a docker compose file which will
     - Create two services (database and api)
     - Spin up the services
     - Share the volume across for the instances
 - Define the database user/pass in the compose
     - Use the same variable for DB credentials in both api and db 

## Build a load balancer
  - Create a base image for your load balancer (e.g. nginx)
  - Configure nginx to 

## Update your docker compose
Update your docker compose and see that it's all running.
