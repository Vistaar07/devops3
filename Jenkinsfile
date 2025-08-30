pipeline {
    agent any

    tools {
        nodejs 'NodeJS-24'
    }

    stages {
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