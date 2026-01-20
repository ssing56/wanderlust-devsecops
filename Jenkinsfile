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
