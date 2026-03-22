pipeline {
    agent any  // Use any available agent

    tools {
        maven 'Maven'  // Ensure this matches the name configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/narasimhaa44/Devops.git'
            }
        }

        stage('Build') {
            steps {
                dir('maven4gradle'){
                  sh 'mvn clean package'  // Run Maven build
                }
            }
        }

        stage('Test') {
            steps {
                  dir('maven4gradle'){
                      sh 'mvn test'  // Run unit tests
                }
            }
        }

        stage('Run Application') {
            steps {
                    sh 'mvn exec:java -Dexec.mainClass="com.example.App"'
            }
        }

        
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
