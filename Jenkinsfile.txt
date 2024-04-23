pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests using JUnit FOR THE SECOND RUN BY HADI'
                
                echo 'Running integration tests using Selenium'
            }
            post {
                success {
                    emailext attachLog: true, 
                    body: 'Unit and Integration Tests passed successfully', 
                    subject: 'Tests Success', 
                    to: 'hadirastin88@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                    body: 'Unit and Integration Tests failed', 
                    subject: 'Tests Failure', 
                    to: 'hadirastin88@gmail.com'
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code using SonarQube'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP'
            }
            post {
                success {
                    emailext attachLog: true, 
                    body: 'Security Scan passed successfully', 
                    subject: 'Security Scan Success', 
                    to: 'hadirastin88@gmail.com'
                }
                failure {
                    emailext attachLog: true, 
                    body: 'Security Scan failed', 
                    subject: 'Security Scan Failure', 
                    to: 'hadirastin88@gmail.com'
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging server (AWS EC2 instance)'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production server (AWS EC2 instance)'
            }
        }
    }
    
    post {
        success {
            emailext attachLog: true, 
            body: 'Pipeline succeeded', 
            subject: 'Pipeline Success', 
            to: 'hadirastin88@gmail.com'
        }
        failure {
            // Send notification email with failure status and logs as attachment
            emailext attachLog: true, 
            body: 'Pipeline failed', 
            subject: 'Pipeline Failure', 
            to: 'hadirastin88@gmail.com'
        }
    }
}
