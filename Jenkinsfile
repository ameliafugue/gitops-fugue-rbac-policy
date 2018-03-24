pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
      additionalBuildArgs '-v /var/run/docker.sock:/var/run/docker.sock'
    }
    
  }
  stages {
    stage('Stage One') {
      steps {
        sh 'id'
      }
    }
  }
}
