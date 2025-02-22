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
                // Use Bash for this stage
                sh '''
                    #!/bin/bash
                    python3 -m venv venv
                    source venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Build') {
            steps {
                // Use Bash for this stage
                sh '''
                    #!/bin/bash
                    source venv/bin/activate
                    python src/main.py
                '''
            }
        }
        stage('Test') {
            steps {
                // Use Bash for this stage
                sh '''
                    #!/bin/bash
                    source venv/bin/activate
                    pytest src/test_main.py
                '''
            }
        }
    }
    post {
        always {
            cleanWs() // Clean the workspace after the pipeline is finished
        }
    }
}