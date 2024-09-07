pipeline {
  agent any
  environment {
    SONARQUBE_SERVER = 'SonarCLoud'
    SONAR_TOKEN = credentials('SonarCLoud')
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
