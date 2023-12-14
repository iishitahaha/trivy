pipeline {
    agent any
    stages {
        stage('Vulnerability Scan - Docker Trivy') {
            steps {
            //--------------------------replace variable  token_github on file trivy-image-scan.sh
            withCredentials([string(credentialsId: 'trivyy', variable: 'TOKEN')]) {
            sh "sed -i 's#token_github#${TOKEN}#g' trivy-image-scan.sh"      
            sh "sudo bash trivy-image-scan.sh"
        }
       }
        }
    }
}
