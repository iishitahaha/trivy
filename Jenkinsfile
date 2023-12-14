pipeline {
    agent any
    stages {
        stage('Configure Docker') {
            steps {
            sh '''
            sudo apt update
            sudo apt-get install docker.io
            sudo systemctl enable docker.service
            sudo systemctl start docker.service
            sudo usermod -aG docker jenkins
            sudo chmod 666 /var/run/docker.sock
            '''
        }
       }
        }
    }
}
