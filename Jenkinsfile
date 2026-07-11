pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Isax127/wordpress-docker.git', branch: 'main'
            }
        }
        stage('Down') {
            steps {
                sh '/usr/local/bin/docker-compose down || true'
            }
        }
        stage('Up') {
            steps {
                sh '/usr/local/bin/docker-compose up -d'
            }
        }
        stage('Verify') {
            steps {
                sh '/usr/bin/docker ps'
            }
        }
    }
}
