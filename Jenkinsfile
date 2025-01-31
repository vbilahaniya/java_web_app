pipeline {
    agent any
     tools {
        maven 'Maven-3.9.9' 
    }


    stages {
         stage('git clone') {
            steps {
              git branch: 'main', credentialsId: 'jenkins-ssh', url: 'git@github.com:vbilahaniya/java_web_app.git'
            }
        }

         stage('build') {
            steps {
              sh 'mvn clean package'
            }
        }
        stage('Sonarqube') {
            steps {
             withSonarQubeEnv('SonarQube-7') {
                sh 'mvn sonar:sonar'
               }
            }      
        }
        stage('upload artifactory') {
            steps {
              nexusArtifactUploader artifacts: [[artifactId: 'my-web-app', classifier: '', file: 'target/my-web-app.war', type: 'war']], credentialsId: 'jenkins-nexus', groupId: 'com.example', nexusUrl: '3.111.39.30:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'java_web_app_repo', version: '1.0-SNAPSHOT'
              


            }

    }
}
