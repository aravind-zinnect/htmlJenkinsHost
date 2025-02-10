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

                    bat """
                    echo Checking if index.html exists...
                    if exist "${webServerPath}index.html" (
                        echo Backing up old index.html...
                        copy "${webServerPath}index.html" "${webServerPath}index_backup.html"
                    )

                    echo Copying new index.html...
                    copy /Y "${jenkinsWorkspace}\\index.html" "${webServerPath}"
                    if %ERRORLEVEL% neq 0 (
                        echo ERROR: Copy failed! Restoring old index.html...
                        copy /Y "${webServerPath}index_backup.html" "${webServerPath}index.html"
                    )
                    """
                }
            }
        }
    }
}
