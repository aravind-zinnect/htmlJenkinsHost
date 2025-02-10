pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aravind-zinnect/htmlJenkinsHost.git'
            }
        }

        stage('Deploy to Web Server') {
            steps {
                script {
                    def webServerPath = "C:\\Program Files\\Apache24\\htdocs\\"
                    def jenkinsWorkspace = env.WORKSPACE  // Get Jenkins workspace path
                    bat "if exist \"${webServerPath}index.html\" del /F /Q \"${webServerPath}index.html\""
                    bat "copy /Y \"${jenkinsWorkspace}\\index.html\" \"${webServerPath}\""
                }
            }
        }
    }
}
