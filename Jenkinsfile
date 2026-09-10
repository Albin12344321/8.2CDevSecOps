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
                sh 'npm install'
            }
        }
        stage('Run Security Audit') {
            steps {
                sh 'npm audit || true'
            }
        }
    }
}