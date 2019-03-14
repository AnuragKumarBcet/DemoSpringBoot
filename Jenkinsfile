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
    }
    stage('Compile') {
      steps {
        sh 'mvn compile'
      }
    }
    stage('test') {
      steps {
        sh 'mvn test'
      }
       post{
        always{
          junit '**/surefire-reports/**/*.xml'
        }
      }
    }
    stage('package') {
      steps {
        sh 'mvn package'
      }
      post{
        success{
          archiveArtifacts 'target/*.hpi,target/*jpi,target/*.jar'
        }
      }
    }
  }
}
