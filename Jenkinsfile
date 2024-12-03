pipeline {
    agent { label 'linux-node' }
    
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'https://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@github.com/bfelician0/node-webapp.git', 
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

