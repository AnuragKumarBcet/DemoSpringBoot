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
      post {
        always {
          junit '**/surefire-reports/**/*.xml'

        }

      }
      steps {
        sh 'mvn test'
      }
    }
    stage('package') {
      post {
        success {
          archiveArtifacts 'target/*.hpi,target/*jpi,target/*.jar'

        }

      }
      steps {
        sh 'mvn package'
      }
    }
  }
}