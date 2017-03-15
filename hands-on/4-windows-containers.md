# 4 - Windows containers

Windows containers now fully supported with docker - you can now utilize the same deployment model and tooling but are able to run familar and known capabilities in the container. These exercises will give you some hands-on on Windows container and see how to built various windows base images for your deployments.

Make sure you've installed docker on your machine and enabled the Windows Container feature.
**You can do this exercise on either a virtualized Hyper-V container or on your Windows 10 -box.**

## Getting started

 - Switch to Windows containers on your docker for windows. 
 - Install the powershell modules required for running the docker host
 ```
Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force
Install-Module -Name DockerMsftProvider -Force
Install-Package -Name docker -ProviderName DockerMsftProvider -Force
Restart-Computer -Force
 ```
  - NB: If you're running the docker host in a Hyper-V environment, you'd want to expose this to the host-Os

```
# Open firewall port 2375 on server 2016 to be able to set remote docker host
netsh advfirewall firewall add rule name="docker engine" dir=in action=allow protocol=TCP localport=2375

# Configure Docker daemon to listen on both pipe and TCP (replaces docker --register-service invocation above)
Stop-Service docker
dockerd --unregister-service
dockerd -H npipe:// -H 0.0.0.0:2375 --register-service
Start-Service docker

# Invoke this on your HOST OS
# $env:DOCKER_HOST = "<ip-address-of-vm>:2375"
```

Make sure docker is running and working

## Windows server core
You will now build a base out from windows server core.

  - Fetch a base image for server core
  - Switch the powershell in your dockerfile
  - Build and see that it runs OK
  - Install .Net 4.5
  - Build the container
  - Find the size of your server core image
  

## Nano server with IIS

You will now build your first nano server. Nano server is the cloud first server and is more lightweight.
 
 - Start with a clean base image for nano server
 - Set shell to powershell
 - Install IIS
 - Install ASP.Net 4.5
 - Build the container
 - Compare the size to the servercore
 - Download a git repo from internet (of your choice) - explore commands (explore some powershell cmds)
 - Remove the default web site
 - Add a custom web site (with naming of your choice ), port 80 and a physical path where you put your web app
 - Expose the iis port and application in your docker file
 - Build and start the container
 - See that your web app is running






