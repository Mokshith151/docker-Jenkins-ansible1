pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "mokshi11/staticapp-ansi"
    }

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/Mokshith151/docker-Jenkins-ansible1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Docker Login') {
            steps {
                sh 'docker login -u mokshi11 -p Mokshith#123'
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
