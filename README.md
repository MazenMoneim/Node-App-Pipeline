# NodeJS-Todo-App
## Project Overview
* Deploy a Node.js application to manage our todo list.
* Implement a CI/CD pipeline using Jenkins, Docker, GitHub Webhooks, and Docker Hub.
* Provision Jenkins server and Docker agent on AWS cloud.
## Project Description
### </> Provisioning Instances on AWS Cloud
* Initially, we provisioned two instances on AWS—one for running Jenkins and another for Docker.
* We utilized the userdata option to execute a script during system boot. This script installed OpenJDK 17 and set up the Jenkins server on the first instance. Similarly, we installed Docker on the second instance.
* Security groups were configured to allow specific ports: 8080 (Jenkins server), 50000 (Jenkins agent), and 8000 (our application).
### </> Configuring Jenkins Server
* After provisioning, we established webhooks between GitHub and Jenkins to trigger our pipeline on every commit.
* Additionally, we added our Docker server as an agent in Jenkins. To ensure connectivity, we allowed the “security -> agents -> tcp” option.
### </> Configuring the Pipeline
#####  - Our Jenkinsfile consists of four stages:
- Code Stage: Ensures that our Jenkins server reacts to events on the main branch of our repository.
- Build and Test stage: Establishes our build process using a Dockerfile to create our image.
- Login and Push: Logs in to Docker Hub and pushes our image with a specific tag.
- Deploy: Runs our application using an HTTP URL.
  
####

![WebHook](https://github.com/MazenMoneim/node-app/assets/135109542/59f094d9-bba4-4ec1-b6e9-a648befe9f40)

