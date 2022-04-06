pipeline {
    agent any
    stages {
        stage('Clean') {
            steps {
                sh 'docker stop hk-helloworld && docker rm hk-helloworld || true'
            }
        }
      stage('Build') {
            steps {
                sh 'docker build --tag hk-helloworld:$BUILD_NUMBER .'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run --name hk-helloworld -p 1338:1338 hk-helloworld:$BUILD_NUMBER node /var/www/index.js &'
            }
        }
        
    }
}
