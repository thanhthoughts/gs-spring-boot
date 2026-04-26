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
                sh 'mkdir -p target'
                sh 'echo "HW6 Springboot Artifact" > target/helloworld-1.0.0.jar'
            }
        }
        stage('Push to Nexus') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '192.168.1.165:8082',
                    groupId: 'com.example',
                    version: '1.0.0',
                    repository: 'maven-releases',
                    credentialsId: 'nexus-credentials',
                    artifacts: [
                        [artifactId: 'helloworld', classifier: '', file: 'target/helloworld-1.0.0.jar', type: 'jar']
                    ]
                )
            }
        }
    }
}
