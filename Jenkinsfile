pipeline{

	agent {label 'linux'}

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-hub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/Genchuwu/test.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t evgeni2003/flask:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push evgeni2003/flask:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
