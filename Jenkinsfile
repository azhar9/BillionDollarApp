pipeline {
  agent any

  stages {
    
    stage('Build') {
      steps {
        sh"""
        ll
        cd app
        npm run build
        ll
        cd ..
        """
      }
    }

    stage('Zipping') {
      steps {
        sh"""
        cd app
        zip -r build_${BUILD_NUMBER}.zip build
        ll
        cd ..
        """
      }
    }
  }
}
