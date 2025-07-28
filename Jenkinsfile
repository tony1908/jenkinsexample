pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'toony1908/jenkinsexample'
    }

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/tony1908/jenkinsexample.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    dockerImage = docker.build(DOCKER_IMAGE)
                }
            }
            post {
                success {
                    sh 'echo "Docker image built successfully"'
                }
                failure {
                    sh 'echo "Failed to build Docker image"'
                }
            }
        }

        stage('Push') {
            steps {
                script{
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub') {
                        dockerImage.push('latest')
                    }
                }
            }
            post {
                success {
                    sh 'echo "Docker image pushed successfully"'
                }
                failure {
                    sh 'echo "Failed to push Docker image"'
                }
            }
        }
    }
}