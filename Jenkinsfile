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

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'

                    withSonarQubeEnv('SonarQube') {
                        bat """
                            "${scannerHome}\\bin\\sonar-scanner.bat" ^
                            -Dsonar.projectKey=P2-Sonarqube-demo ^
                            -Dsonar.projectName=P2-Sonarqube-demo ^
                            -Dsonar.sources=.
                        """
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'P2 Jenkins Pipeline completed successfully.'
        }
        failure {
            echo 'P2 Jenkins Pipeline failed.'
        }
    }
}
