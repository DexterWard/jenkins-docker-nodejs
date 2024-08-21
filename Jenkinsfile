pipeline {
    agent {
        docker {
            image 'node:14-alpine' // Docker image Node.js
            args '-p 5001:5001'
        }
    }
    environment {
        APP_NAME = 'my-node-app'
    }
    stages {        
        stage('Install Dependencies') {
            steps {
                
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                
                sh 'npm test'
            }
        }
        stage('Run Application') {
            steps {
                // Execute the app
                sh 'npm start &'
                // wait 5 seconds to start appp
                sh 'sleep 60'
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}




















