pipeline {
    agent any

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
                sh 'echo "Building the application"'
            }
        }
    }
}