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
                sh 'whoami'
            }
        }
        stage('Deploy Docker Compose Stacks') {
            steps {
                script {
                    def composeFiles = sh(
                        script: "find ${env.DOCKER_DIR} -name 'docker-compose.yml'",
                        returnStdout: true
                    ).trim().split("\n")

                    for (file in composeFiles) {
                        echo "Processing compose file: ${file}"
                        
                        def dirPath = file.substring(0, file.lastIndexOf('/'))
                        
                        dir(dirPath) {
                            echo "Pulling images"
                            sh 'docker-compose pull'

                            echo "Bringing up services"
                            sh 'docker-compose up -d --remove-orphans'
                        }
                    }
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
