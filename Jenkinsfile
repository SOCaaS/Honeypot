pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                echo 'Installing....'
                sh 'curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose'
                sh 'chmod +x /usr/bin/docker-compose'
                sh '/usr/bin/docker-compose --version'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'echo ${BUILD_NUMBER}'
                sh 'docker build --network main-overlay -f Dockerfile --tag cowrie-server:${BUILD_NUMBER} .'
           }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'TAG=${BUILD_NUMBER} /usr/bin/docker-compose down -v'
            }
        }
    }
}
