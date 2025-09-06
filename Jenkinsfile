pipeline {
    agent { label 'agent_20.81' }

    environment {
        DOCKER_DIR = '/home/ubuntu/docker/osticket'
    }

    stages {
        stage('Print Docker Directory') {
            steps {
                echo "Docker directory path is: ${env.DOCKER_DIR}"
            }
        }

        stage('List Docker Folder Contents') {
            steps {
                sh 'ls -la /home/ubuntu/docker/osticket'
                sh 'whoami'
            }
        }

        stage('Deploy osticket Docker Compose') {
            steps {
                dir("${env.DOCKER_DIR}") {
                    echo "Pulling images for osticket"
                    sh 'docker compose pull'

                    echo "Bringing up osticket services"
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully 🎉'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}
