pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ritika-node-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f ritika-container || true
                docker run -d -p 3000:3000 --name ritika-container ritika-node-app
                '''
            }
        }
    }

    post {
        success {
            echo "Application Deployed Successfully"
        }
        failure {
            echo "Deployment Failed"
        }
    }
}
