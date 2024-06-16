pipeline {
	agent {
		docker{
			image 'composer:latest'
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'composer install'
			}
		}

		stage('Initialize'){
			def dockerHome = tool 'myDocker'
			env.PATH = "${dockerHome}/bin:${env.PATH}"
		}

		stage('Test') {
			steps {
                sh './vendor/bin/phpunit tests'
            }
		}
	}
}