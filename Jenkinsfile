pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''echo "get code from github"
echo "build artifact"'''
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo "deploy to production"'
      }
    }
  }
}