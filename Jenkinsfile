pipeline {
    agent any

    stages {
         stage('git clone') {
            steps {
             git credentialsId: 'jenkins-ssh', url: 'git@github.com:vbilahaniya/java_web_app.git'
            }
        }
        
    }
}
