
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

		stage('Package') {
			steps {
				sh 'mvn package -DskipTests'
			}
		}
		
		stage('Build Docker Image') {
			steps {
				//docker build -t tobiasmarkj/jenkins-devops-microservice:$env.BUILD_TAG
				script {
					dockerImage = docker.build("tobiasmarkj/jenkins-devops-microservice:${env.BUILD_TAG}");
				}
			}
		}
		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
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
