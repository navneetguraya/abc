pipeline {
    agent any
    tools {
        maven 'maven'
        }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main',
                credentialsId: '22f9a7d0-eada-44ac-a939-48e27c7e868f',
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
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
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
