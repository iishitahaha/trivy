pipeline {
    agent any
    stages {
        stage('Configure Trivy') {
            steps {
                sh '''
                sudo apt-get install wget apt-transport-https gnupg lsb-release
                wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
                echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
                sudo apt-get update
                sudo apt-get install trivy
                '''
            }
        }
        stage('Docker pull') {
            agent {
                docker {
                    image ${Docker_image}
                }
            }
        }
        stage('Trivy Scan') {
            steps {
                sh """
                trivy image "${Docker_image}"
                """
            }
        }
        }
    }
