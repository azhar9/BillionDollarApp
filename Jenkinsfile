pipeline {
  agent any

  stages {
    
    stage('Build') {
      steps {
        sh"""
        ls
        cd app
        npm install
        npm run build
        ls
        cd ..
        """
      }
    }

    stage('Zipping') {
      steps {
        sh"""
        cd app
        zip -r build_${BUILD_NUMBER}.zip build
        ls
        cp build_${BUILD_NUMBER}.zip /var/jenkins_home/builds/
        cd ..
        """
      }
    }
  }
}
