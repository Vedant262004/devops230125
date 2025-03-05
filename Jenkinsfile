pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Vedant262004/devops230125.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'  // Use appropriate build command (e.g., npm, gradle)
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        
    }
     post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for errors.'
        }
    }
}
