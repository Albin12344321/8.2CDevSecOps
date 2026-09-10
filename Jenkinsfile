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
        stage('Run Security Audit') {
            steps {
                bat 'npm audit'
            }
        }
    }
}