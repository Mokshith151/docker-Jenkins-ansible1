# DevOps Static Application Deployment

## Tools Used

- Docker
- Jenkins
- Ansible
- GitHub
- DockerHub

## Architecture

Jenkins + Ansible (Master)
|
|----> Worker Node (Docker)

## Pipeline Flow

1. Developer pushes code to GitHub
2. Jenkins triggers pipeline
3. Jenkins builds Docker image
4. Image pushed to DockerHub
5. Jenkins runs Ansible playbook
6. Ansible deploys container in worker node

## Access Application

http://WORKER_PUBLIC_IP:8005