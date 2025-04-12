pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Use 'sh' to run Maven on Linux
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                // Use forward-slashes for Linux paths; adjust the docker command accordingly
                sh 'docker cp target/Exp7.war tomcat_container:/usr/local/tomcat/webapps'
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
