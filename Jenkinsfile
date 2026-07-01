stage('Remove Old Container') {
    steps {
        sh 'docker rm -f demo-web || true'
    }
}

stage('Run Container') {
    steps {
        sh 'docker run -d --name demo-web -p 8088:80 jenkins-demo:v1'
    }
}

stage('Verify Running Container') {
    steps {
        sh 'docker ps'
    }
}
