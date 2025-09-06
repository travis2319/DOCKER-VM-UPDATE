pipeline {
    agent { label 'agent_20.81' }

    environment {
        DOCKER_DIR = '/home/ubuntu/docker'
    }

    stages {
        stage('Print Docker Directory') {
            steps {
                echo "Docker directory path is: ${env.DOCKER_DIR}"
            }
        }

        stage('List Docker Folder Contents') {
            steps {
                sh 'ls -la /home/ubuntu/docker'
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
