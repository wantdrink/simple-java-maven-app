pipeline {
    agent {
        kubernetes {
            // Define your containers within the pod template
            containerTemplate {
                name 'maven'
                image 'maven:3.9.6-eclipse-temurin-17'
                // Add command and args to ensure it stays running and doesn't terminate prematurely
                // This is a common pattern for Kubernetes Pods
                command 'cat'
                args ' '
            }
            defaultContainer 'maven'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}