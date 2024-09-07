pipeline {
  agent any
  environment {
    SONARQUBE_SERVER = 'SonarCloud'
    SONAR_TOKEN = credentials('SonarCloud')
  }
  stages {
    stage('Build'){
      steps {
        script {
          sh './gradlew sonarqube'
        }
        
      }
    }
    stage ('Quality Gate'){
      steps {
        script {
          timeout(time: 1, unit: 'HOURS') {
            waitForQualityGate()
          }
        }
      }
    }
  }
}
