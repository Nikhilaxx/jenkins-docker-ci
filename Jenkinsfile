pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh '''
                    export PATH="/usr/local/bin:$PATH"
                    docker build -t jenkins-nginx-app .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                    export PATH="/usr/local/bin:$PATH"
                    docker rm -f jenkins-nginx-container || true
                    docker run -d \
                        --name jenkins-nginx-container \
                        -p 8082:80 \
                        jenkins-nginx-app
                '''
            }
        }
    }
}
