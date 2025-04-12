pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Run Maven using a Docker command
                sh '''
                docker run --rm -v "$PWD":/workspace -v "$HOME/.m2":/root/.m2 -w /workspace maven:3.8.6-openjdk-11 mvn clean package
                '''
            }
        }
        stage('Deploy') {
            steps {
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
