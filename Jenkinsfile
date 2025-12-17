pipeline {
    agent any

    tools {
        maven 'M2_HOME'
    }

    stages {
        stage('MAVEN VERSION') {
            steps {
                bat 'mvn -version'
            }
        }
    }
}
