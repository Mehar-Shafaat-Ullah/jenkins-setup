pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Mehar-Shafaat-Ullah/jenkins-setup.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t my-onprem-app .'
            }
        }

        stage('Deploy') {
            steps {
                // Stop and remove old container if it exists
                sh 'docker stop my-app || true'
                sh 'docker rm my-app || true'
                // Run the new one
                sh 'docker run -d --name my-app -p 8081:80 my-onprem-app'
            }
        }
    }
}
