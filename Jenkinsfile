pipeline {
    agent { label 'PROD' }
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
        stage('Integration test') {
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }
        stage('Maven Build stage') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}