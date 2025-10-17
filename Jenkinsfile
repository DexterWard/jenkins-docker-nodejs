pipeline {
    agent{
        docker{
            image 'node:14-alpine' //Image Docker Node.js
            args '-p 5001:5001'
        }
    }
    
    stages {        
        stage('Install Dependencies') {
            steps {
                sudo chown -R 122:126 "/.npm"
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




















