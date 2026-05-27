pipeline {
    agent any

    tools {
        dockerTool 'my-docker' // This matches the name you gave it in Tools
    }

    stages {

        stage('Clone Code') {
            steps {
                echo 'Cloning repository...'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t devops-node-app .'
                }
            }
        }

        stage('Stop Old Container') {
            steps {
                script {
                    sh 'docker stop nodeapp || true'
                    sh 'docker rm nodeapp || true'
                }
            }
        }

        stage('Run New Container') {
            steps {
                script {
                    sh 'docker run -d -p 3000:3000 --name nodeapp devops-node-app'
                }
            }
        }
    }
}
