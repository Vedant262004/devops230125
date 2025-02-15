pipeline {
    agent any
    tools {
        maven "MAVEN"
        jdk "JDK"
    }

    stages {
        stage('Initialize') {
            steps {
                echo "PATH = ${MAVEN_HOME}/bin:${PATH}"
                echo "MAVEN_HOME = /opt/maven"
            }
        }
        
        stage('Build') {
            steps {
                dir("C:\ProgramData\Jenkins\workspace\Pipeline_job/my-app") {
                    sh 'mvn -B clean package'
                }
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            junit(
                allowEmptyResults: true,
                testResults: '*/test-reports/*.xml'
            )
        }
        failure {
            echo 'Build failed! Investigate the issue.'
        }
    }
}
