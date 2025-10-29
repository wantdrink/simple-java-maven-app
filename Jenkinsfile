pipeline {
    agent {
        label 'maven-jdk' // <-- This must match the Pod Template label!
    }

    tools {
        maven 'M3'
    }

    stages {
        stage('Checkout Code') {
            steps {
                // The source code is automatically checked out by the
                // Kubernetes JNLP container before this stage starts.
                echo 'Source code checked out by the agent.'
                // You can add logic here if you need to set up a specific branch, etc.
            }
        }

        stage('Build') {
            steps {
                container('maven-jdk') {
                    sh '''
                        echo 'start maven'
                        mvn -B clean package
                    '''
                }
            }
        }
    }
}