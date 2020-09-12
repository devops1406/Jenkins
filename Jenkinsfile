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
                stage ('Para 1') {
                    steps {
                        retry(3) {
                            sh ('dummy')
                        }
                    }
                }
                
                stage ('Para 2') {
                    steps {
                         timeout(time: 1, unit: 'MINUTES') {
                            sh ('sleep 2m')
                         }
                    }
                }

            }
        }
                
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
