pipeline {
    agent any

    environment {
        PYTHON = "C:\\Users\\keybl\\AppData\\Local\\Python\\bin\\python.exe"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                // If using SCM, this may be automatic
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                bat "\"%PYTHON%\" -m pip install -r requirements.txt"
            }
        }

        stage('Lint Code') {
            steps {
                echo 'Checking code quality...'
                bat "\"%PYTHON%\" -m pip install flake8"
                bat "\"%PYTHON%\" -m flake8 ."
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                bat "\"%PYTHON%\" -m pytest"
            }
        }

        stage('Run Application') {
            steps {
                echo 'Running application...'
                bat "\"%PYTHON%\" app.py"
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}