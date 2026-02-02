pipeline {
    agent any
    
    options {
        // unit: 'HOURS' büyük harf ve virgül eklendi
        timeout(time: 1, unit: 'HOURS') 
        timestamps() 
        disableConcurrentBuilds() 
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository from Source Control...'
                checkout scm
            }
        }
        
        stage('Build & Test') {
            steps {
                echo "Running tests on branch: ${BRANCH_NAME}"
                // sh komutu içindeki tırnaklara ve parantezlere dikkat
                sh "echo 'Compiling the application and running unit tests...'"
            }
        }
        
        stage('Deploy to Staging') {
            when {
                branch 'develop'
            }
            steps {
                echo ' Deploying to Staging Environment...'
            }
        }
        
        stage('Deploy to Production') {
            when {
                branch 'main'
            }
            steps {
                echo ' Deploying to Production Environment...'
                sh 'echo "Deployment to PROD successful"'
            }
        }
    }
    
    post {
        success {
            echo ' Pipeline completed successfully!'
        }
        failure {
            echo ' Pipeline failed. Checking logs...'
        }
    }
}