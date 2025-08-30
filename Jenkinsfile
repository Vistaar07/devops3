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
                    sh 'npm install'
                }
            }
        }

        stage('Test') {
            steps {
                dir('devops3') {
                    sh 'npm test -- --watchAll=false'
                }
            }
        }

        stage('Build') {
            steps {
                dir('devops3') {
                    sh 'npm run build'
                }
            }
        }

        stage('Serve App') {
            steps {
                dir('devops3') {
                    sh 'npm install serve'
                    sh 'nohup npx serve -s build -l 3000 &'
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