pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
				echo "########## Building stage started"
                bat 'mvn clean compile'
				echo "########## Building stage finished"
            }
        }
		
		stage('Test') {
			steps {
				echo "########## Testing stage started"
				bat 'mvn test'
				echo "########## Testing stage finished"
			}
			post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
		}
		
		stage('Deploy') {
			steps {
				echo "########## Deploying stage started"
				bat 'mvn clean package -DskipTests'
				echo "########## Deploying stage finished"
			}
		}
    }
	post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}