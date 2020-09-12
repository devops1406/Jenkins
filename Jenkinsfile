pipeline {
    
    agent {
        label 'node'
    }
    
    triggers {
        pollSCM '* * * * *'
    }

    stages {
        stage ('Parallel') {
            parallel {
                
                stage('Clone HTML Repo') {
                    steps {
                        git credentialsId: 'SSH_DevOps1406', url: 'https://github.com/DevOps-Company/html.git'
                    }
                }
            
                stage('Copy index.html') {
                    steps {
                        sh 'sudo cp index.html  /var/www/html/' 
                    }
                }
            }
        }
    }
}
