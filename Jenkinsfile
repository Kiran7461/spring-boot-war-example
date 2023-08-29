pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('SCM checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Kiran7461/spring-boot-war-example.git']])
            }
        }
	stage('Sonar stage') {
            steps {
                echo "running sonar scan"
		}
        }
        stage('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('deploy') {
            steps {
               deploy adapters: [tomcat9(credentialsId: 'tomcat9', path: '', url: 'http://35.154.90.88:8080')], contextPath: '/29aug1', war: '**/*.war'
            }
        }    
    }
}


