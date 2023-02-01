pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    stages {
        stage('git checkout') {
            steps {
                git 'https://github.com/Y-Deekshith/counter_app.git'
            }
        }
        stage('Unit test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}