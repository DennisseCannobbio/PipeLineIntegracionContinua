pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        
        stage('Start Server') {
            steps {
                script {
                    sh 'npm start &'
                    sh 'sleep 5'
                    sh 'curl -s http://localhost:3000/users | grep -q "Alice"'
                }
            }
            post {
                always {
                    sh 'pkill -f "node server.js" || true'
                }
            }
        }
    }
    
    post {
        always {
            junit '**/junit.xml'
        }
    }
}