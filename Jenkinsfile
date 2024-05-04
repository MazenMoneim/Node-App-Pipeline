pipeline {
    agent { label 'docker-agent' }
    
    stages{
        stage('code'){
            steps {
                git url: 'https://github.com/MazenMoneim/node-app.git', branch: 'main'
            }
        }
        stage('Build and Test'){
            steps {
                sh 'sudo docker build . -t mazen0/node-app:latest'
            }
        }
        stage('Login and Push Image'){
            steps {
                echo 'logging in to docker hub and pushing image..'
                withCredentials([usernamePassword(credentialsId:'DockerHub',passwordVariable:'DockerHubPassword', usernameVariable:'DockerHubUsername')]) {
                    sh "sudo docker login -u ${env.DockerHubUsername} -p ${env.DockerHubPassword}"
                    sh "sudo docker push mazen0/node-app:latest"
                }    
            }
        }
        stage('Deploy'){
            steps {
                sh 'sudo docker image pull mazen0/node-app:latest'
                sh 'sudo docker run -p 8000:8000 -d mazen0/node-app:latest'
            }
        }
    }
}
