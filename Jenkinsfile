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

        stage('Deploy') {
            steps {
                echo 'Stopping any existing application...'
                bat 'taskkill /F /IM java.exe || echo "No running Java process found"'
                
                echo 'Starting new application...'
                bat 'start /B java -jar target/devops230125.jar'
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
