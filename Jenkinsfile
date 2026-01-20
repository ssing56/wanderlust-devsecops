pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Backend Image') {
            steps {
                dir('backend') {
                    sh 'docker build -t wanderlust-backend:v1 .'
                }
            }
        }

        stage('SonarQube Scan') {
            steps {
                dir('backend') {
                    withSonarQubeEnv('sonarqube') {
                        sh 'sonar-scanner'
                    }
                }
            }
        }
    }
}

