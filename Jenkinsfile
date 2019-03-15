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
    stage('Static code Analysis'){
      steps{
       sh mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=463bfe9ab73a6180d75fe5c97fa45dff62ed2f8a
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
