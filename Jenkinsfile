pipeline {
    agent {
        label 'docker'
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
                sh 'docker build -t jenkins-demo:v1 .'
            }
        }

        stage('List Images') {
            steps {
                sh 'docker images | grep jenkins-demo'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
