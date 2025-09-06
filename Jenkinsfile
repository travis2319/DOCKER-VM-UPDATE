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
                sh 'ls -la ${DOCKER_DIR}'
                sh 'whoami'
            }
        }

        stage('Deploy beszel') {
            steps {
                dir("${DOCKER_DIR}/beszel") {
                    sh 'docker compose pull'
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }
        stage('Deploy rustdesk') {
            steps {
                dir("${DOCKER_DIR}/rustdesk") {
                    sh 'docker compose pull'
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }
        stage('Deploy beszel_agent') {
            steps {
                dir("${DOCKER_DIR}/beszel_agent") {
                    sh 'docker compose pull'
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }

        stage('Deploy meshcentral') {
            steps {
                dir("${DOCKER_DIR}/meshcentral") {
                    sh 'docker compose pull'
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }

        stage('Deploy osticket') {
            steps {
                dir("${DOCKER_DIR}/osticket") {
                    sh 'docker compose pull'
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }
        
        stage('Deploy netx') {
            steps {
                dir("${DOCKER_DIR}/netx") {
                    sh 'docker compose pull'
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }

        stage('Deploy nextcloud') {
            steps {
                dir("${DOCKER_DIR}/nextcloud") {
                    sh 'docker compose pull'
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }

        stage('Deploy portainer') {
            steps {
                dir("${DOCKER_DIR}/portainer") {
                    sh 'docker compose pull'
                    sh 'docker compose up -d --remove-orphans'
                }
            }
        }

        // stage('Deploy immich') {
        //     steps {
        //         dir("${DOCKER_DIR}/immich") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        // stage('Deploy nginx-proxy-manager') {
        //     steps {
        //         dir("${DOCKER_DIR}/nginx-proxy-manager") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        // stage('Deploy uptime') {
        //     steps {
        //         dir("${DOCKER_DIR}/uptime") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        // stage('Deploy shuffle') {
        //     steps {
        //         dir("${DOCKER_DIR}/shuffle") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        // stage('Deploy vaultwarden') {
        //     steps {
        //         dir("${DOCKER_DIR}/vaultwarden") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        // stage('Deploy bookstack') {
        //     steps {
        //         dir("${DOCKER_DIR}/bookstack") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        // stage('Deploy monitoring_prometheus') {
        //     steps {
        //         dir("${DOCKER_DIR}/monitoring_prometheus") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        // stage('Deploy zabbix-docker') {
        //     steps {
        //         dir("${DOCKER_DIR}/zabbix-docker") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        // stage('Deploy thehive_cortex') {
        //     steps {
        //         dir("${DOCKER_DIR}/thehive_cortex") {
        //             sh 'docker compose pull'
        //             //sh 'docker compose up -d --remove-orphans'
        //         }
        //     }
        // }

        stage('Cleanup Temporary Directories') {
            steps {
                sh 'rm -rf /home/ubuntu/docker/*@tmp'
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
