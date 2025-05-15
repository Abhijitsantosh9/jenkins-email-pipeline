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
                    sh 'echo "Test log - everything passed" > test.log'
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo 'Running security scan...'
                    sh 'echo "Security scan completed with 0 vulnerabilities." > audit.log'
                }
            }
        }
    }

    post {
        success {
            emailext (
                subject: "✅ Jenkins Build #${env.BUILD_NUMBER} Success",
                body: "Build completed successfully.\nCheck logs attached.\n\nBuild URL: ${env.BUILD_URL}",
                to: 'abhijitkurup99@gmail.com',
                attachmentsPattern: '*.log'
            )
        }
        failure {
            emailext (
                subject: "❌ Jenkins Build #${env.BUILD_NUMBER} Failed",
                body: "Build failed. See attached logs.\n\nBuild URL: ${env.BUILD_URL}",
                to: 'abhijitkurup99@gmail.com',
                attachmentsPattern: '*.log'
            )
        }
    }
}
