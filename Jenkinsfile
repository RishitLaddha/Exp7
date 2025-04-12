pipeline {
    agent any
    stages {
        stage('Build') {
            // Run Maven build inside a container that has Maven installed
            agent {
                docker {
                    // Use a Maven image that comes with Maven and Java
                    image 'maven:3.8.6-openjdk-11'
                    // Optional: preserve your local Maven repository if needed
                    args '-v $HOME/.m2:/root/.m2'
                }
            }
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                // Use shell command to deploy WAR file to your Tomcat container
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
