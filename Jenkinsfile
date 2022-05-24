pipeline {
  agent any
  stages {
    stage('Source') {
      steps {
        sh 'echo "source the code from github for brach test"'
      }
    }
    stage('Build') {
      steps {
        sh 'echo "build the artifact"'
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            sh 'echo "testing"'
          }
        }
        stage('test services') {
          steps {
            sh 'echo "test services"'
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo "deploy to QA"'
      }
    }
  }
}
