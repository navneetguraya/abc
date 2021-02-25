pipeline {
    agent any
    tools {
        maven 'maven'
        }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main',
                credentialsId: 'e8d0d800-ea2d-43eb-a937-ab0a484cace8',
                url: 'https://github.com/navneetguraya/abc.git'
                }
        }
        stage ('Compile') {
            steps {
                sh 'mvn compile'
                }
            }   
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/workspace/new/*'
            }
        }
        stage ('Creat War File') {
            steps {
                sh 'jar -cf target/*.jar target/*.war'
                }
            }
            stage ('Deploy War File') {
            steps {
                sh "cp target/*.war /etc/apache-tomcat-8.5.61/webapps/"
            }
        }
    }
}
