pipeline {
    agent any
    tools {
        ant 'Ant'
    }
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
                    if not exist lib mkdir lib
                    if not exist lib\\ivy.jar (
                        curl -o lib\\ivy.jar https://repo1.maven.org/maven2/org/apache/ivy/ivy/2.5.2/ivy-2.5.2.jar
                    )
                    ant -f build.xml -lib lib -Dinstaller.version=%INSTALLER_VERSION% retrieve-installer-win32
                """
            }
        }
    }
}
