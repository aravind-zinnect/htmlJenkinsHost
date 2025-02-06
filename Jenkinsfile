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
                    def webServerPath = 'C:\\Apache24\\htdocs\\' // Change if using IIS
                    bat "copy index.html ${webServerPath}"
                }
            }
        }
    }
}
