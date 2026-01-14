pipeline {
    agent any

    environment {
        VENV = "venv"
    }

    stages {

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/USERNAME/python-jenkins-gitcheckout.git'
            }
        }

        stage('Create Virtual Environment') {
            steps {
                sh 'python3 -m venv $VENV'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                . $VENV/bin/activate
                pip install --upgrade pip
                pip install flask
                '''
            }
        }

        stage('Run Application') {
            steps {
                sh '''
                pkill -f app.py || true
                nohup $VENV/bin/python app.py > app.log 2>&1 &
                '''
            }
        }
    }
}
