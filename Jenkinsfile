pipeline {
    agent any  // Runs on any available Jenkins agent
    tools{
        maven "MAVEN"
        jdk "JDK"
    }

    stages {
        stage('Intialize') {
            steps {
                echo "PATH=${MAVEN_HOME}/bin:${PATH}"
                echo "MAVEN_HOME = /opt/maven"
            }
        }

        stage('Build') {
            steps {
                dir("/var/lib/jenkins/workspace/https")
                sh 'mvn -B -DskipTests clean package'  // Example build command
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
