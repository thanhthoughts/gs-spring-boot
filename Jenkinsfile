pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                // Make the maven wrapper executable
                sh 'chmod +x mvnw'
                // Clean and package the application into a fat jar
                sh './mvnw clean package'
            }
        }
    }
}
