pipeline {
    agent any

    stages {
        stage('Pull SCM') {
            steps {
                git branch: 'gh-pages', url: 'https://github.com/aryapramudika/springboot-app.git'
            }
        }
        
        stage('Containerized Apps') {
            steps {
                sh'''
                docker build -t pramudika/springboot-app:v3 .
                '''
            }
        }

        stage('Push to Registry') {
            steps {
                sh'''
                docker push pramudika/springboot-app:v3
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