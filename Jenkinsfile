pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('credentials')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/username/name.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t username/repo:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push username/repo:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
