pipeline {
    agent any

    stages {
        stage('Checkout desde Git') {
            steps {
                checkout scm
            }
        }

        stage('Detener ambiente (docker compose down)') {
            steps {
                sh 'docker compose down || true'
            }
        }

        stage('Levantar ambiente (docker compose up -d)') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Verificar despliegue (docker ps)') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Despliegue exitoso: WordPress disponible en http://localhost:8080'
        }
        failure {
            echo 'El despliegue falló, revisar logs.'
        }
    }
}
