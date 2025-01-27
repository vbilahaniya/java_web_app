pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
              script {
                  sh git branch: 'main', credentialsId: 'jenkins-ssh', url: 'git@github.com:vbilahaniya/java_web_app.git'
                }
                
                
            }
        }
        
    }
}
