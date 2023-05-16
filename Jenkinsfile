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
        }
    }                                                                                                                                                                                                                                                                  
}
