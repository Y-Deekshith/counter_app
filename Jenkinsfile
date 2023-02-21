pipeline {
    agent { label 'DEV' }
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
        stage('static code analysis') {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonarqube') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        // stage('Quality check') {
        //     steps {
        //         script {
        //                 waitForQualityGate abortPipeline: false, credentialsId: 'sonarcube-auth'
        //         }
        //     }
        // }
        // stage('Uplode artifact') {
        //     steps {
        //         script {
        //             nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/Uber.jar', type: 'jar']], credentialsId: 'nexus-auth', groupId: 'com.example', nexusUrl: 'ec2-54-87-5-160.compute-1.amazonaws.com:8081/', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '1.0-SNAPSHOT'
        //         }
        //     }
        // }
    }
}