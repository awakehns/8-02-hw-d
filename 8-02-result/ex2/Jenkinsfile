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
        stage('Build') {
            steps {
                sh '/usr/bin/docker build .' 
            }
        }   
    }
}
