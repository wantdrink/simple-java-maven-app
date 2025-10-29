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
                         mvn -B clean package \\
                        -Dhttp.proxyHost=proxy-nasa.svcs.entsvcs.com \\
                        -Dhttp.proxyPort=8080 \\
                        -Dhttps.proxyHost=proxy-nasa.svcs.entsvcs.com \\
                        -Dhttps.proxyPort=8080 \\
                        -Dhttp.nonProxyHosts="localhost|127.0.0.1|*.cluster.local"
                    '''
                }
            }
        }
    }
}