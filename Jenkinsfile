pipeline {
    agent any

    stages {

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Janakiraman0207/jenkins-deployment.git'
            }
        }

        stage('Build') {
            steps {
                sh '''
                echo "Installing dependencies"
                pip3 install --user flask
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Stopping old application"
                pkill -f app.py || true

                echo "Starting application"
                nohup python3 app.py > app.log 2>&1 &
                '''
            }
        }
    }
}
