pipeline {
    agent { label 'PROD' }
    tools {
        maven 'Maven3'
    }
    stages {
        stage('git checkout') {
            steps {
                git credentialsId: 'github_auth', url: 'git@github.com:Y-Deekshith/counter_app.git'
            }
        }
        stage('Unit test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}