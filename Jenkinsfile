pipeline {
    agent any
    
    tools {
        maven 'M2_HOME'  // Doit correspondre au nom de ta configuration Maven dans Jenkins
    }
    
    stages {
        stage('GIT') {
            steps {
                git branch: 'ProjetSpring',
                    url: 'https://github.com/Ahmedbenjannet/Devops.git'
            }
        }
        
        stage('MVN CLEAN') {
            steps {
                bat 'mvn clean'
            }
        }
        
        stage('MVN COMPILE') {
            steps {
                bat 'mvn compile'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {  // Nom exact de ta configuration SonarQube dans Jenkins
                    withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
                        bat """
                        mvn sonar:sonar ^
                        -Dsonar.projectKey=devops-project ^
                        -Dsonar.projectName=DevOps ^
                        -Dsonar.host.url=http://192.168.56.10:9000 ^
                        -Dsonar.token=%SONAR_TOKEN%
                        """
                    }
                }
            }
        }
    }
}
