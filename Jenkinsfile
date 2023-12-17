
//DECLARATIVE
pipeline {
	agent any
	//agent { docker { image 'maven:3.8.6-jdk-11'}}
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				
				echo "PATH $PATH"
				echo "BUILD_NUMBER $env.BUILD_NUMBER"
				echo "BUILD_ID $env.BUILD_ID"
				echo "JOB_NAME $env.JOB_NAME"
				echo "BUILD_TAG $env.BUILD_TAG"
				echo "BUILD_URL $env.BUILD_URL"
				echo "mvn --version"
				sh 'mvn --version'
				echo "docker version"
				sh 'docker version'
			}
		}
		stage('Compile') {
			steps {
				echo "mvn clean compile"
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				echo "mvn test"
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
				sh 'mvn failsafe:integration-test failsafe:verify'
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
