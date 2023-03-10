pipeline {
	agent any
    environment {
        DOCKERHUB_CREDENTIALS=credentials('sathu21-dockerhub')
             }
    stages {
        stage('Build-SathusanGanesathasan') {
            steps {
		    // bat 'docker build -t sathutest/maven:3.5.0'
                script {
                   MY_CONTAINER = bat(script: '@docker run -d -i maven:3.5.0', returnStdout: true).trim()
                   bat "docker exec ${MY_CONTAINER} maven --version "
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
        
