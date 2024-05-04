# node-todo-app
### Overview of the porject
* Deploy NodeJs application to save our todo-list.
* Implementing CI/CD pipeline using Jenkins, Docker, Github-Webhooks and Docker-Hub.
* Provisioing Jenkins server and Docker agent on aws cloud provider.
### Project Description
##### -> Provision two instance on aws cloud
* First, we provisioned two instance in aws to run jenkins and docker, we used `userdata option to run script file while system is booting to install open-jdk-17 and jenkins server in the first instance, after that we used the same approche to install docker.
* We configured secureity group on aws to allow ports like 8080 (jenkins-server-port), 50000 (jenkins-agent-port) and our application running on port 8000.
##### -> Configure Jenkins server
* After the provisioning, we configured our webhook in both sides (Github and Jenkins) to make sure in every commit our pipeline would be estaplished.
* Furthermore, we add our docker-server as an agent in jenkins-server, in this step we should allow security -> agents -> tcp option to make sure our connection would be estaplished.
##### -> Configure pipeline
* we configured our jenkins file with four stages:
-> Code Stage: to make sure our jenkins server manipulate the events on the main branch in our repo.
-> Build and Test stage: to establish our bulid process using docker file to create our image.
-> Login and Push: to login on docker hub to push our image with specific tag.
-> Deploy: to run our application using http url.
####

![WebHook](https://github.com/MazenMoneim/node-app/assets/135109542/59f094d9-bba4-4ec1-b6e9-a648befe9f40)

