pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/rahulsanghavimca009/springboot-hello.git'
            }
        }

        stage('Fix Permissions') {
            steps {
                sh 'chmod +x mvnw'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t springboot-hello .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop springboot-hello || true'
                sh 'docker rm springboot-hello || true'
                sh 'docker run -d -p 8081:8081 --name springboot-hello springboot-hello'
            }
        }
    }
}
