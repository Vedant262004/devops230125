pipeline {
    agent any  // Runs on any available Jenkins agent

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/Vedant262004/devops230125.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'  // Example build command
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'  // Run unit tests
            }
        }

        stage('Deploy') {
            steps {
                sh 'scp target/app.jar user@server:/deploy/path'
            }
        }
    }
  post {
        success {
            slackSend channel: '#deployments', message: 'Deployment Successful 🎉'
        }
        failure {
            slackSend channel: '#alerts', message: 'Deployment Failed ❌'
        }
    }
}
