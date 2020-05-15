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

    stage('CI') {
      parallel {
        stage('CI') {
          steps {
            echo 'Iniciando CI process'
            sh 'ls -ltr'
          }
        }

        stage('image') {
          steps {
            sh 'docker build -t e1rubs/webserver:v4 .'
          }
        }

        stage('container') {
          steps {
            sh 'docker run -d --name WebServerCI -p 83:80 e1rubs/webserver:v4'
          }
        }

      }
    }

    stage('validate') {
      steps {
        sh 'docker iamges'
        sh 'docker ps'
      }
    }

  }
}