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
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'TAG=${BUILD_NUMBER} /usr/bin/docker-compose -p "honeypot" up -d --build'
            }
        }
    }
}
