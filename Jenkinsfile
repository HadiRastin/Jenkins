pipeline {
    agent any
    
    environment {
        DIRECTORY_PATH = 'C:/Users/Hadi/Desktop/Computer Science/2024/Professional Practice/OnTrck/Working/5.1P'

        TESTING_ENVIRONMENT = 'testing_environment'
        PRODUCTION_ENVIRONMENT = 'Hadi Rastin' 
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from the directory path specified by the environment variable: ${DIRECTORY_PATH}"
                echo "Compiling the code and generating any necessary artifacts"
            }
        }
        
        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
            }
        }
        
        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code"
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying the application to a testing environment specified by the environment variable: ${TESTING_ENVIRONMENT}"
            }
        }
        
        stage('Approval') {
            steps {
                echo "Waiting for manual approval..."
                sleep(time: 10, unit: 'SECONDS') 
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the production environment: ${PRODUCTION_ENVIRONMENT}"
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
