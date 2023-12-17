
//DECLARATIVE
pipeline {
	agent any
	//agent { docker { image 'maven:3.8.6-jdk-11'}}
	stages {
		stage('Build') {
			steps {
				//echo "mvn --version"
				//sh 'mvn --version'
				echo "BUILD_NUMBER $env.BUILD_NUMBER"
				echo "BUILD_ID $env.BUILD_ID"
				echo "JOB_NAME $env.JOB_NAME"
				echo "BUILD_TAG $env.BUILD_TAG"
				echo "BUILD_URL $env.BUILD_URL"
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
