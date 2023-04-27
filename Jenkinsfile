pipeline {
  agent none
  stages {
    stage('Build & Test') {
      agent {
        docker {
          image 'nikhilpathania/jenkins_ssh_agent'
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
        docker {
          image 'nikhilpathania/jenkins_ssh_agent'
        }

      }
      steps {
        unstash 'build-test-artifacts'
        junit '**/target/surefire-reports/TEST-*.xml'
        sh 'ls -l'
        archiveArtifacts(artifacts: '**/target/helloworld-example-0.1.0.jar', onlyIfSuccessful: true)
      }
    }

  }
}