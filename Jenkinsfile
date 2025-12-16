pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validation Docker Compose') {
            steps {
                sh 'docker compose -f infra/docker/compose.yml config'
            }
        }

        stage('Validation Nginx') {
            steps {
                sh '''
                sudo apt-get update && sudo apt-get install -y nginx
                nginx -t -c $WORKSPACE/infra/docker/nginx.conf
                '''
            }
        }

        stage('Sécurité basique') {
            steps {
                sh '''
                docker run --rm aquasec/trivy config --exit-code 0 --severity HIGH infra/docker/
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline terminé avec succès'
        }
        failure {
            echo '❌ Erreur détectée, vérifiez les logs'
        }
    }
}
