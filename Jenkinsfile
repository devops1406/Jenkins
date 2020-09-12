pipeline {
    
    environment {
        MyName = 'Chetan'
    }
    
    agent {
        label 'node2'
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
                
                stage ('Para 2') {
                    steps {
                         timeout(time: 3, unit: 'MINUTES') {
                            sh ('sleep 1m')
                         }
                    }
                }

            }
        }
            
        stage('Copy index.html') {
            steps {
                sh 'sudo cp index.html  /var/www/html/' 
            }
        }
        
    }
}
