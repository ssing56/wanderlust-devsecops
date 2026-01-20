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
                sh '''
                  cd backend
                  docker build -t wanderlust-backend:v1 .
                '''
            }
        }

        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh '''
                      cd backend
                      sonar-scanner
                    '''
                }
            }
        }
    }
}

