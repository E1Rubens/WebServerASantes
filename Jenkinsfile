pipeline {
  agent any
  stages {
    stage('content') {
      parallel {
        stage('view content') {
          steps {
            sh 'ls -la'
          }
        }

        stage('versions') {
          steps {
            sh '''git --version
'''
            sh 'docker --version'
          }
        }

      }
    }

    stage('messsage') {
      steps {
        echo 'Iniciando Pipeline'
      }
    }

  }
}