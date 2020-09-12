pipeline {
    
    environment {
        MyName = 'Chetan'
    }
    
    agent {
        label 'node'
    }
    
    triggers {
        pollSCM '* * * * *'
    }

    stages {
        
        stage ('Parallel') {
            parallel {
                stage ('Para 1') {
                    steps {
                        sh ('echo "Paralled Satge 1 $MyName"')
                    }
                }
                
                stage ('Para 2') {
                    steps {
                        sh ('echo "Paralled Stage 2 $MyName"')
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
