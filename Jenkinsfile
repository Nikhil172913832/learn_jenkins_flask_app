pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Nikhil172913832/learn_jenkins_flask_app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                #!/bin/bash
                python3 -m venv .venv
                source .venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                bash -c "
                source .venv/bin/activate && \
                pip install --upgrade pip && \
                pip install -r requirements.txt
                "
                '''

            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-jenkins-app .'
            }
        }
    }
}
