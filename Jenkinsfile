pipeline {
    agent {
        label 'docker'
    }

    stages {
        stage('Check Agent') {
            steps {
                sh 'echo "Running on agent:"'
                sh 'hostname'
                sh 'pwd'
            }
        }
    }
}
