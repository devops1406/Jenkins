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
                        sh ('echo "Para2"')
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

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
