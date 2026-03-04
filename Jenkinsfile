pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/harishmurali7418-prog/devops-demo'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f devops-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8090:8080 --name devops-container devops-demo'
            }
        }
    }
}
