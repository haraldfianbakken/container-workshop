# 3 - Docker and docker compose

You will now get some hands-on with using images from the docker-hub and built incremental images. This hands-on will not use Visual studio, so you will get practical exercises in editing the docker files and building/starting containers manually. You will also use docker compose to create more complex scenarios for spinning up dependencies in a docker environment.

For the simplicity we will base our images on public images from the public repos on <a href="https://hub.docker.com">https://hub.docker.com</a>.

For inspiration for images, check out : <a href="https://hub.docker.com/explore/">Explore repositories</a>

**NB:** Make sure you've installed the docker for windows <a href="https://docs.docker.com/docker-for-windows/install/#download-docker-for-windows">here</a>

## Build your first container (database)
 - Find a database (base) image of your choice (postgres,mssql,mysql)
 - Create a simple database schema 
     - One table : blobid, blobname, isProcessed (bool), result (text/json)
 - Extend your container with DB-initializiation
     - Create a database and a user with admin rights to that DB
     - Execute *.sql scripts for initializiation    
 - Build and start your container
 - See that you're able to connect to the SQL instance and that your DB has been created

## Build your second container
 - Find a base image of your choice
 - Extend the image with a file storage from your host , this will be used for storing blobs
 - Create an API for posting blobs (nodejs/aspnetcore)
 - When receiving the blob, put a record into the database and the blob in the storage. Fire off an async method for analyzing the image content (e.g. cognitive serivces) and write the result back to the DB when it's processed.
 - Build and spin up the container and see that your API is working

## Create a third container
 - Find a base image for hosting static web-content
 - Create a simple SPA appliation to display an upload form for files.
 - Serve web requests to your SPA app and a simple -app that ships images to your api.
 - Extend the image and include the SPA application when building the docker
 - Build and spin up the docker container and see that your SPA app is running

## Create your docker compose
 - Create a docker compose file which will
     - Create three services (database, api, web)
     - Spin up the services
     - Share the volume across for the instances
 - Define the database user/pass in the compose
     - Use the same variable for DB credentials in both api and db 
 - Spin up all three containers and see that they run correctly using docker-compose

## Build a load balancer
  - Create a base image for your load balancer (e.g. nginx)
  - Configure LB to route traffic to your api and web app
  - Create a route that maps all traffic for /api and sends it to app container
  - Route all other traffic to web container (apart from sql)

## Update your docker compose
Update your docker compose with your load balancer, spin it up and see that it's all running and serving requests for one port.

You should now be able to spin up and serve traffic for http://localhost - serving both / -> (web app) /api/* (api) and localhost:sqlport (db).

