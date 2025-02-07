pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/aravind-zinnect/simple-repo3.git'
            }
        }

        stage('Deploy to Web Server') {
            steps {
                script {
                    def webServerPath = 'C:\Program Files\Apache24\htdocs'
                    bat "copy index.html ${webServerPath}"
                }
            }
        }
    }
}
