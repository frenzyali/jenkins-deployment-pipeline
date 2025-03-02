pipeline {
    agent any

    stages {
        stage('Pull Docker Image') {
            steps {
                script {
                    sh 'docker pull alihussain312008/simple-webapp:latest'
                }
            }
        }

        stage('Deploy to EC2') {
            steps {
                sshagent(['ec2-ssh-key']) {
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@3.82.193.5 "docker stop simple-webapp || true"'
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@3.82.193.5 "docker rm simple-webapp || true"'
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@3.82.193.5 "docker run -d --name simple-webapp -p 9090:80 alihussain312008/simple-webapp:latest"'
                }
            }
        }
    }
}


