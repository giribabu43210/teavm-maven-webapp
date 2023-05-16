pipeline {
    agent any

    stages {
        stage('Download') {
            steps {
                checkout scmGit(branches: [[name: '*/batch15']], extensions: [], userRemoteConfigs: [[credentialsId: 'github_cred', url: 'https://github.com/devopsdeepdive/teavm-maven-webapp.git']])
            }
        }
        stage('Build') {
            steps {
                sh 'mvn compile'  
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'  
            }  
        }
        stage('package') {
            steps {
                sh 'mvn package'  
            }   
        stage('deploy') {
            steps {
                sshagent(['tomcat_server']) {
                  sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/teavm-maven-webapp/target/teavm-maven-webapp-1.2-RELEASE.war ubuntu@172.31.9.84:/opt/tomcat/apache-tomcat-9.0.75/webapps'              
            
                }            
            }        
        }
    }                                                                                                                                                                                                                                                                  
}
