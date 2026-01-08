pipeline {
    agent any
   
    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/vbilahaniya/java_web_app.git'
            }
        }
    }
}
