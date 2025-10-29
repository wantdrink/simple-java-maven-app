pipeline {
    agent {
        // Change the label from 'default-4vh29' (or similar)
        // to a specific Kubernetes container configuration
        kubernetes {
            // Use a standard Java/Maven image
            // jenkins/maven is a good option
            // 'maven:3.9.6-eclipse-temurin-17' is also a reliable choice
            containerTemplate {
                name 'maven'
                image 'maven:3.9.6-eclipse-temurin-17'
                // Add other config if needed
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