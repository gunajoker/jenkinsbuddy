pipeline {
    agent any
    parameters {
        string(name: 'INSTALLER_VERSION', defaultValue: '1.0.0', description: 'Installer version')
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello'
            }
        }
        stage('Retrieve Installer') {
            when {
                expression { isUnix() == false }
            }
            steps {
                bat """
                    ant -f build.xml -Dinstaller.version=%INSTALLER_VERSION% retrieve-installer-win32
                """
            }
        }
    }
}
