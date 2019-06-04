pipeline {
  agent any
  stages {
    stage('Source') {
      steps {
        sh 'echo "Develop"'
      }
    }
    stage('Build') {
      steps {
        sh 'echo "build the artifact Develop"'
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo "deploy to Develop"'
      }
    }
  }
}
