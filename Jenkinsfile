pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                echo 'Code cloned from GitHub'
            }
        }

        stage('Build Docker Image') {
    steps {
        sh '''
        pwd
        ls -la
        docker build -t myhtmlapp:v2 .
        '''
    }
}

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f myweb2 || true
                docker run -d --name myweb2 -p 8081:80 myhtmlapp:v2
                '''
            }
        }
    }
}
