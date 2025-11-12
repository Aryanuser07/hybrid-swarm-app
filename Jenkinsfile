pipeline {
    agent any

    environment {
        // Tells Jenkins to target the Docker daemon inside your VM
        DOCKER_HOST = 'tcp://172.26.18.69:2375'
    }

    stages {
        stage('Checkout') {
            steps {
                // This pulls the docker-compose.yml from GitHub
                checkout scm
            }
        }
        stage('Deploy to Swarm') {
            steps {
                // This command now runs on your host, but targets the VM
                bat 'docker stack deploy -c docker-compose.yml hybrid_app'
            }
        }
    }
}
