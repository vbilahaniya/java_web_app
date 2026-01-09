pipeline {
    agent any
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
    }
}
