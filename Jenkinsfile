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
      }
    }
    stage('Compile') {
      steps {
        sh 'mvn compile'
      }
    }
  }
}
