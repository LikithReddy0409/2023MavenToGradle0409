pipeline {
    agent any  // Use any available agent

    tools {
        maven 'Maven'  // Ensure this matches the name configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/LikithReddy0409/2023MavenToGradle0409.git'
            }
        }

      stage('Build') {
    steps {
        sh 'mvn clean package -DskipTests'
    }
}
        stage('Test') {
            steps {
          
                      sh 'mvn test'  // Run unit tests
                
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
