
//DECLARATIVE
pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
	} post {
		always {
			echo "Run always"
		}
		success {
			echo "Run on success"
		}
		failure {
			echo "Run on failure"
		}

	}
	
}
