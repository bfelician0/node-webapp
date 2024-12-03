pipeline {
    agent { label 'linux-node' }
    
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'bfelician0', 
                    url: 'https://github.com/bfeliciano/node-webapp.git', 
                    branch: 'main'
            }
        }
        
        stage('Build') {
            steps {
                script {
                    docker.build('node-webapp:latest')
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    docker.image('node-webapp:latest').run('-d -p 3000:3000')
                }
            }
        }
    }
}

