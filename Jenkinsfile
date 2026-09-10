pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Repository checked out by Jenkins SCM'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                bat 'npm test || exit /b 0'
            }
            post {
                always {
                    emailext(
                        subject: "Test Stage - ${currentBuild.currentResult}: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: "The Test stage finished with status: ${currentBuild.currentResult}.\n\nSee attached log for details.",
                        to: 's225737313@deakin.edu.au',
                        attachLog: true
                    )
                }
            }
        }
        stage('Run Security Audit') {
            steps {
                bat 'npm audit || exit /b 0'
            }
            post {
                always {
                    emailext(
                        subject: "Security Scan - ${currentBuild.currentResult}: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: "The Security Scan stage finished with status: ${currentBuild.currentResult}.\n\nSee attached log for details.",
                        to: 's225737313@deakin.edu.au',
                        attachLog: true
                    )
                }
            }
        }
    }
}