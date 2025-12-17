pipeline {
    agent any

    tools {
        maven 'M2_HOME'
    }

    stages {

        stage('Checkout Git') {
            steps {
                git 'https://github.com/Ahmedbenjannet/Devops.git'
            }
        }

        stage('Maven Clean Compile') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat '''
                    mvn sonar:sonar ^
                    -Dsonar.projectKey=devops-project ^
                    -Dsonar.projectName=DevOps ^
                    -Dsonar.host.url=http://localhost:9000 ^
                    -Dsonar.login=SONAR_TOKEN
                    '''
                }
            }
        }
    }
}
