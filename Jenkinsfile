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
                    docker.build(DOCKER_IMAGE)
                }
            }
        }
    }
}