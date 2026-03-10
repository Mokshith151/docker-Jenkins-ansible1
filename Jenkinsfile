pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "mokshi11/staticapp-ansi:latest"
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials')
    }

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Mokshith151/docker-Jenkins-ansible1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Docker Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh 'ansible-playbook -i inventory.ini playbook.yml'
            }
        }

    }

    post {
        always {
            sh 'docker logout || true'
        }
        success {
            echo '✅ Deployment successful! App running on Worker:8005'
        }
        failure {
            echo '❌ Pipeline failed — check console output above.'
        }
    }
}
