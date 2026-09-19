pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build completed successfully.'
            }
        }

        stage('Docker Build') {
            steps {
                bat '"C:\\Users\\LENOVO\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" build -t p3-jenkins-demo:latest .'
            }
        }

        stage('Verify Docker Image') {
            steps {
                bat '"C:\\Users\\LENOVO\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" images p3-jenkins-demo'
            }
        }
    }

    post {
        success {
            echo 'P3 Docker image build completed successfully.'
        }

        failure {
            echo 'P3 Docker image build failed.'
        }
    }
}