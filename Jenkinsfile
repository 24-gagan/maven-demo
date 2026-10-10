pipeline {
    agent { label 'Windows_Agent' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat 'mvn -B clean compile'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn -B test'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn -B package -DskipTests'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success { echo 'Build pass hua' }
        failure { echo 'Build fail hua' }
    }
}