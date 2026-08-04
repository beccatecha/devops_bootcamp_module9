#!/usr/bin.env groovy

pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application..."

                }
            }
        }
        stage("build") {
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    def shellCmd = "bash ./server-cmds.sh"
                    sshagent(['ec2-server-key']) {
                    sh "scp server-cmds.sh ec2-user@54.184.87.157:/home/ec2-user"
                        sh "scp docker-compose.yaml ec2-user@54.184.87.157:/home/ec2-user"
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@54.184.87.157 ${shellCmd}"
                    }
                }
            }
        }               
    }
} 
