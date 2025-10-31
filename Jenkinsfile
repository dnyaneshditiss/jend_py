pipeline {
	agent any
	environment {
		DOCKER_IMAGE ='hello-world-python:1.0'// Dopcker image name
		}
	stages {
	    stage('Checkout') {
			steps{ 
			   git branch: 'main', url:
					'https://github.com/dnyaneshditiss/jend_py.git'
			}
		}
		stage('Docker Build') {
			steps {
				script {
					if (fileExists('Dockerfile')) {
						sh "docker build -t ${env.DOCKER_IMAGE} ."	
					}
					else {
						error "Dockerfile not found"
					}
				}
			}
		}
		stage('Docker Run (optional)') {
			steps {
				sh "docker run --rm ${env.DOCKER_IMAGE}"
		}
}
	}

	post {
		success {
			echo 'Python image built'
			}

		failure {
			echo 'Docker build failed'
			}
}
}
