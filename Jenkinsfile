pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/rahulsanghavimca009/springboot-hello.git'
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
                sh 'docker run -d -p 8080:8080 --name springboot-hello springboot-hello'
            }
        }
    }
}