pipeline {
  agent any

  stages {
    
    stage('Build') {
      steps {
        sh 'docker build -t billiondollarapp:${BUILD_NUMBER} .'
      }
    }

    stage('Push') {
      steps {
        sh 'echo "hello world"'
      }
    }
  }
}
