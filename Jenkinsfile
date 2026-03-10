pipeline {
agent any

```
environment {
    DOCKER_IMAGE = "mokshith151/static-app"
}

stages {

    stage('Clone Repository') {
        steps {
            git branch: 'main', url: 'https://github.com/Mokshith151/docker-Jenkins-ansible1.git'
        }
    }

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t $DOCKER_IMAGE .'
        }
    }

    stage('Docker Login') {
        steps {
            sh 'docker login -u mokshith151 -p YOUR_DOCKERHUB_PASSWORD'
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
```

}
