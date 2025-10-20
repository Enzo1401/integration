pipeline {
    agent {
        docker { image 'python:3.11' }
    }
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Set up Python') {
            steps {
                sh 'python --version'
                sh 'pip install --upgrade pip'
                sh 'pip install pytest'
            }
        }
        stage('Run tests') {
            steps {
                sh 'pytest ci_demo/tests'
            }
        }
    }
    post {
        success { echo '✅ Pipeline completed successfully!' }
        failure { echo '❌ Pipeline failed.' }
    }
}
