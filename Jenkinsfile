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
                bat 'mvn clean package'
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
            echo 'Pipeline executed successfully! Deployment completed.'
        }
        failure {
            echo 'Pipeline failed. Check the logs for errors.'
        }
    }
}
