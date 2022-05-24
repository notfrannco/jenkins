pipeline {
  agent none
  stages {
    stage('Build & Test') {
      agent {
        node {
          label 'docker'
        }

      }
      steps {
        sh '''git clone https://github.com/begining-jenkins-blue-ocean/example-maven-project.git
cd example-maven-project/
mvn -Dmaven.test.failure.ignore clean package'''
        stash(name: 'build-test-artifacts', includes: '**/target/surefire-reports/TEST-*.xml,target/*.jar')
      }
    }

    stage('Report & Publish') {
      agent {
        node {
          label 'docker'
        }

      }
      steps {
        unstash 'build-test-artifacts'
        //junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts(artifacts: 'target/*.jar', onlyIfSuccessful: true)
      }
    }

  }
}
