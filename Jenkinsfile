pipeline {
agent any
    environment {
        DOCKERHUB_CREDENTIALS=credentials('sathu21-dockerhub')
             }
    stages {
        stage('Build-SathusanGanesathasan') {
            steps {
                script {
                   MY_CONTAINER = bat(script: '@docker run -d -i python:3.10.7-alpine', returnStdout: true).trim()
                   bat "docker exec ${MY_CONTAINER} python --version "
                   bat "docker rm -f ${MY_CONTAINER}"
                        }
                    }
                }
        stage('Login-SathusanGanesathasan') {
            steps {
                bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    } 
    stage('Push-SathusanGanesathasan') {

			steps {
				bat 'docker push python:3.10.7-alpine/sathu'
			}
		}
    }
      post {
        always {
                bat 'docker logout'
        }
      }        
            }
        
