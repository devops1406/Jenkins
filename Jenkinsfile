pipeline {
    
    environment {
        MyName = """${ sh(returnStdout: true, script: './shell.sh') } """
    }
    
    agent {
        label 'node2'
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
                        sh label: 'shell', script: '''
                            #!/bin/bash
                            echo "My Name is $MyName"
                        '''
                    }
                }

            }
        }
            
        stage('Copy index.html') {
            steps {
                sh 'sudo cp index.html  /var/www/html/' 
                script {
                    Var1 = sh label: '', returnStdout: true, script: 'pwd'
                }
                    sh 'echo "No of chars $Var1"'
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
