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
            post {
                success {
                    echo 'Tests passed successfully!'
                }
                failure {
                    echo 'Tests failed! Check the test results for more information.'
                    error 'Test stage failed'
                }
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
            junit 'test-results/*.xml' 
            
            sh 'echo "Pipeline executed at $(date)" > pipeline-report.txt'
            sh 'echo "Test results: $PIPELINE_RESULT" >> pipeline-report.txt'
            archiveArtifacts artifacts: 'pipeline-report.txt', fingerprint: true
        }
    }
}