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
                    echo Checking if file exists...
                    if exist "${webServerPath}index.html" (
                        echo Deleting old index.html...
                        del /F /Q "${webServerPath}index.html"
                    ) else (
                        echo No existing index.html found.
                    )

                    echo Copying new index.html...
                    copy /Y "${jenkinsWorkspace}\\index.html" "${webServerPath}"
                    if %ERRORLEVEL% neq 0 echo ERROR: Failed to copy file!
                    """
                }
            }
        }
    }
}
