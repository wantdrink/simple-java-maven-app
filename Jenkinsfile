pipeline {
    agent {
        label 'maven-jdk' // <-- This must match the Pod Template label!
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
                        # Set the proxy environment variables
                        echo "Running Maven build inside the Jelastic Maven JDK 21 container..."
                        mvn -B -DskipTests clean package
                    '''
                }
            }
        }
    }
}