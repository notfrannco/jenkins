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
        sh 'git clone https://github.com/nikhilpathania/hello-world-example.git'
        sh 'cd hello-world-example/'
        sh 'cd hello-world-example/; mvn -Dmaven.test.failure.ignore clean package'
        stash(name: 'build-test-artifacts', includes: '**/target/surefire-reports/TEST-*.xml,**/target/helloworld-example-0.1.0.jar')
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
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts(artifacts: '**/target/surefire-reports/TEST-*.xml,**/target/helloworld-example-0.1.0.jar', onlyIfSuccessful: true)
      }
    }

  }
}