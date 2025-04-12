pipeline {
    agent any
    triggers {
        // Poll SCM every 5 minutes
        pollSCM('H/5 * * * *')
    }
    stages {
        stage('Build') {
            steps {
                // Adjust to use 'sh' if your environment is Unix-based
                bat 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                // Adjust the command syntax if necessary; here assuming Windows batch commands
                bat 'docker cp target\\Exp7.war tomcat_container:/usr/local/tomcat/webapps'
            }
        }
    }
    post {
        success {
            echo 'Build and deployment succeeded.'
        }
        failure {
            echo 'Build or deployment failed.'
        }
    }
}
