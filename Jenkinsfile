pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/RahulVaidya1030/jenkins_demo.git' // Replace with your repo
            }
        }
        stage('Setup Environment') {
            steps {
                sh 'python3 -m venv venv'
                sh 'source venv/bin/activate'
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Build') {
            steps {
                sh 'source venv/bin/activate'
                sh 'python src/main.py'
            }
        }
        stage('Test') {
            steps {
                sh 'source venv/bin/activate'
                sh 'pytest src/test_main.py'
            }
        }
    }
    post {
        always {
            cleanWs() // Clean the workspace after the pipeline is finished
        }
    }
}