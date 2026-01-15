pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')  // This checks for changes every minutes.
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
		stage('artifact uploader') {
            steps {
               nexusArtifactUploader artifacts: [[artifactId: 'my-web-app', classifier: '', file: 'target/my-web-app-1.0-SNAPSHOT.war', type: 'war']], credentialsId: 'nexus-jenkins', groupId: 'com.example', nexusUrl: '13.127.245.252:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'java_web_app', version: '1.0-SNAPSHOT'
            }
        }
		stage('deploy on dev') {
            steps {
               sshagent(['dev-jenkins']) {
                   sh 'scp -o StrictHostKeyChecking=no target/my-web-app-1.0-SNAPSHOT.war ec2-user@13.201.121.197:/opt/tomcat/apache-tomcat-9.0.113/webapps'
                }
            }
        }
    }
}
