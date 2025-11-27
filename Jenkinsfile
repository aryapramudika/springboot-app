pipeline {
    agent any

    stages {
        stage('Pull SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/aryapramudika/springboot-app.git'
            }
        }
        
        stage('Containerized Apps') {
            steps {
                sh'''
                docker build -t pramudika/springboot-app .
                '''
            }
        }

        stage('Push to Registry') {
            steps {
                sh'''
                docker push pramudika/springboot-app
                '''
            }
        }

        stage('Deploy Apps') {
            steps {
                sh'''
                kubectl apply -f manifest/
                '''
            }
        }   
    }
}