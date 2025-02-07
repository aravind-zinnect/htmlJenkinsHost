pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/aravind-zinnect/htmlJenkinsHost.git'  // Use the correct repo
            }
        }

        stage('Deploy to Web Server') {
            steps {
                script {
                    def webServerPath = "C:\\Program Files\\Apache24\\htdocs\\"
                    bat "del /F /Q \"${webServerPath}index.html\""  // Delete old file
                    bat "copy /Y index.html \"${webServerPath}\""  // Copy new file
                }
            }
        }
    }
}
