#!/usr/bin/env groovy

pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Test') {
            steps {
                sh '/usr/local/go/bin/go test .'
            }
        }
        stage('Build GO binary') {
            steps {
                sh 'CGO_ENABLED=0 GOOS=linux /usr/local/go/bin/go build -a -installsuffix nocgo -o app .'
            }
        }
        stage('Push to Nexus anonymous') {
            steps {
                sh "curl -v -u admin:admin --upload-file app http://127.0.0.1:8081/repository/8-02-hw-nexux-raw-hosted/app"
            }
        }
    }
}
