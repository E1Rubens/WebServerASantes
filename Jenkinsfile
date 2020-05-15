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

    stage('imagen') {
      steps {
        echo 'Iniciando CI process'
        sh 'docker build -t 1rubs/webserver:v4 .'
      }
    }

    stage('container') {
      steps {
        sh 'docker images'
        sh 'docker run -d --name WebServerCI -p 50:80 1rubs/webserver:v4'
      }
    }

    stage('validate') {
      parallel {
        stage('validate') {
          steps {
            echo 'validating image and container'
          }
        }

        stage('imagen') {
          steps {
            sh 'docker images'
          }
        }

        stage('error') {
          steps {
            sh 'docker ps'
          }
        }

      }
    }

  }
}