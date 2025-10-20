pipeline {
    agent any

    environment {
        VENV_DIR = "venv"
    }

    stages {
        stage('Checkout') {
            steps {
                echo '🔄 Cloning repository...'
                checkout scm
            }
        }

        stage('Set up Python') {
            steps {
                echo '🐍 Setting up Python environment...'
                sh "python3 -m venv ${VENV_DIR}"
                sh ". ${VENV_DIR}/bin/activate && pip install --upgrade pip"
                sh ". ${VENV_DIR}/bin/activate && pip install pytest"
            }
        }

        stage('Run tests') {
            steps {
                echo '🧪 Running tests...'
                sh ". ${VENV_DIR}/bin/activate && pytest -v ci_demo/tests"
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed.'
        }
    }
}
