pipeline {
agent any
    
environment {
    DOCKER_IMAGE = "mokshi11/staticapp-ansi"
}

stages {

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t $DOCKER_IMAGE .'
        }
    }

   stage('Docker Login') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-cred',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS')]) {
            sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
        }
    }
}

    stage('Push Docker Image') {
        steps {
            sh 'docker push $DOCKER_IMAGE'
        }
    }

    stage('Deploy using Ansible') {
        steps {
            sh 'ansible-playbook -i inventory playbook.yml'
        }
    }

}

}
