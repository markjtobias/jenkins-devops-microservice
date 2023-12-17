
//DECLARATIVE
pipeline {
	//agent any
	agent { docker { image 'maven:3.8.6-jdk-11'}}
	stages {
		stage('Build') {
			steps {
				echo "mvn --version"
				sh 'mvn --version'
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
	} 
	post {
		always {
			echo "Run always."
		}
		success {
			echo "Run on success."
		}
		failure {
			echo "Run on failure."
		}

	}
	
}
