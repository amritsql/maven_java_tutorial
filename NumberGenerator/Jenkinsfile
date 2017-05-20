pipeline {
    agent master
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
        stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = %PATH%"
                    echo "M2_HOME = %M2_HOME%"
                '''
            }
        }

        stage ('Build') {
            steps {
                bat 'mvn -Dmaven.test.failure.ignore=true install'
            }
            post {
                success {
                    junit 'target\surefire-reports\**\*.xml'
                }
            }
        }
    }
}