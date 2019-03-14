pipeline {
  agent {
    node {
      label 'localhost'
    }

  }
  stages {
    stage('Clean') {
      steps {
        sh 'mvn clean'
      }
      post{
        success{
          archiveArtifacts 'target/*.hpi target/*.jpi target/*.jar'
        }
        always{
          junit '**/surefire-reports/**/*.xml'
        }
      }
    }
    stage('Compile') {
      steps {
        sh 'mvn compile'
      }
    }
  }
}
