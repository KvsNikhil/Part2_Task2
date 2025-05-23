pipeline {
    agent any

    environment {
        RECIPIENT = 'your_email@example.com' // Set this to your test email
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                script {
                    try {
                        echo 'Running tests...'
                        // simulate test (success or failure)
                        bat 'exit 0'
                        currentBuild.result = 'SUCCESS'
                    } catch (e) {
                        currentBuild.result = 'FAILURE'
                        throw e
                    }
                }
            }
            post {
                always {
                    emailext(
                        subject: "Test Stage: ${currentBuild.result}",
                        body: "The Test stage has completed with status: ${currentBuild.result}. See attached logs.",
                        to: "${env.RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    try {
                        echo 'Running security scan...'
                        // simulate scan
                        bat 'exit 0'
                        currentBuild.result = 'SUCCESS'
                    } catch (e) {
                        currentBuild.result = 'FAILURE'
                        throw e
                    }
                }
            }
            post {
                always {
                    emailext(
                        subject: "Security Scan Stage: ${currentBuild.result}",
                        body: "The Security Scan stage has completed with status: ${currentBuild.result}. See attached logs.",
                        to: "${env.RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
    }
}