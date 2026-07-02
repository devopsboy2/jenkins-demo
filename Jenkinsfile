pipeline {
    agent {
        label 'docker'
    }

    environment {
        IMAGE_NAME = "tudtech/jenkins-demo"
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {

        stage('Verify Workspace') {
            steps {
                sh 'echo "Workspace:"'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Check Docker') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
            }
        }

        stage('List Images') {
            steps {
                sh 'docker images | grep jenkins-demo'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f demo-web || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name demo-web -p 8088:80 ${IMAGE_NAME}:${IMAGE_TAG}'
            }
        }

        stage('Verify Running Container') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
