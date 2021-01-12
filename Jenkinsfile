pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                echo 'Installing....'
                sh 'apt update'
                sh 'apt install -y docker-compose'

            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'          
            }
        }
    }
}