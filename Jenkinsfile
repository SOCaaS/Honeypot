pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                echo 'Installing....'
                sh '''#!/bin/bash
                    if [ ! -f /usr/bin/docker-compose ]; then
                        curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
                        chmod +x /usr/bin/docker-compose
                        /usr/bin/docker-compose --version
                    else 
                        echo "There is noting to be downloaded!"
                    fi
                '''
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
