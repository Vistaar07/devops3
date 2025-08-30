pipeline {
    agent any
 
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Vistaar07/devops3.git'
            }
        }
 
        stage('Install Dependencies') {
            steps {
                dir('devops3') {
                    bat 'npm install'
                }
            }
        }
 
        stage('Build / Run') {
            steps {
                dir('devops3') {
                    bat 'npm start'
                }
            }
        }

        stage('Serve App') { 
            steps { 
                dir('devops3') { 
                    bat 'npm install -g serve' 
                    bat 'serve -s build -l 3000 &' 
                } 
            } 
        } 
    } 
 
    post { 
        always { 
            echo 'Pipeline finished' 
        } 
    } 
}
 