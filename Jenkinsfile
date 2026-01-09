pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')  // This checks for changes every minute.
    }
    tools {
        maven 'Maven-3.9.12'
    }
   
    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/vbilahaniya/java_web_app.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
				
            }
        }
        stage('Sonarqube') {
            steps {
                withSonarQubeEnv('SonarQube-8') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
