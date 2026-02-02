pipeline {
    agent any

    stages{
        stage('Build') {
            steps {
                echo 'Checking Files...'
                sh 'ls -la'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing if index.html exists...'
                // index.html dosyası var mı diye kontrol et, yoksa hata ver
                sh 'test -f index.html'
                echo 'Yes, index.html is here'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application'
            }
        }
    }
}