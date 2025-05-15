pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    // Simulate test log
                    sh '''
                    echo "Test log - everything passed" > test.log
                    '''
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo 'Running security scan...'
                    // Simulate audit log
                    sh '''
                    echo "Security scan completed with 0 vulnerabilities." > audit.log
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete.'
        }
        success {
            emailext (
                subject: "✅ Build Passed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The pipeline ran successfully.\n\nJob: ${env.JOB_NAME}\nBuild: ${env.BUILD_URL}",
                attachmentsPattern: 'test.log,audit.log',
                to: 'abhijitkurup99@gmail.com'
            )
        }
        failure {
            emailext (
                subject: "❌ Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The pipeline failed. Check the logs.\n\nJob: ${env.JOB_NAME}\nBuild: ${env.BUILD_URL}",
                attachmentsPattern: 'test.log,audit.log',
                to: 'abhijitkurup99@gmail.com'
            )
        }
    }
}
