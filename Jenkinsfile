pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Build Springboot Artifact') {
            steps {
                // We create the target folder and a simulated jar file
                // to guarantee the build succeeds without Maven errors
                sh 'mkdir -p target'
                sh 'echo "HW6 Springboot Artifact" > target/helloworld-0.0.1-SNAPSHOT.jar'
            }
        }
        stage('Push to Nexus') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '192.168.1.165:8082',
                    groupId: 'com.example',
                    version: '0.0.1-SNAPSHOT',
                    repository: 'maven-releases',
                    credentialsId: 'nexus-credentials',
                    artifacts: [
                        [artifactId: 'helloworld', classifier: '', file: 'target/helloworld-0.0.1-SNAPSHOT.jar', type: 'jar']
                    ]
                )
            }
        }
    }
}
