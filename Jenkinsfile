pipeline {
    agent any

    stages {

        stage('Setup Virtual Environment') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate'
            }
        }

        stage('Upgrade pip') {
            steps {
                sh '. venv/bin/activate && python3 -m pip install --upgrade pip'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '. venv/bin/activate && python3 -m pip install -r requirements.txt'
            }
        }

        stage('Build') {
            steps {
                sh '. venv/bin/activate && python3 main.py build'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
