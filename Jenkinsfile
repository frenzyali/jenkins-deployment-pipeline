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
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@3.82.193.5 "docker stop simple_python_app || true"'
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@3.82.193.5 "docker rm simple_python_app || true"'
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@3.82.193.5 "docker run -d -p 9999:9999 --name simple_python_app alihussain312008/simple-webapp"'
                }
            }
        }
    }
}


