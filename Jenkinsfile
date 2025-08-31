pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

        stage('List Directory') {
            steps {
                dir('/var/jenkins_home/VM-DOCKER-UPDATE') {
                    sh 'ls -lh'
                }
            }
        }
    }
}
