pipeline {
    agent any

    stages {

        stage('Show Workspace') {
            steps {
                sh '''
                pwd
                ls -la
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t devopspro:v2 .
                '''
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                docker rm -f myweb || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d --name myweb -p 8081:80 devopspro:v2
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful'
        }

        failure {
            echo 'Deployment Failed'
        }
    }
}
