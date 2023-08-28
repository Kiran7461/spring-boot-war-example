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
               deploy adapters: [tomcat9(credentialsId: 'tomcat9', path: '', url: 'http://15.207.85.136:8080')], contextPath: '/pipe', war: '**/*.war'
            }
        }    
    }
}


