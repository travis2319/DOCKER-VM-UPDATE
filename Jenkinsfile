pipeline {
    agent {
        label 'agent_20.81'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                // Example: git branch: 'main', url: 'https://github.com/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                // Example: sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example: sh 'mvn test'
            }
        }

        stage('Docker Build & Push') {
            steps {
                echo 'Building and pushing Docker image...'
                // Example:
                // sh 'docker build -t your-image:latest .'
                // sh 'docker push your-image:latest'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Example: sh 'kubectl apply -f deployment.yaml'
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
