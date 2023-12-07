pipeline {
    agent any 
    
    stages {
        stage ('Build') {
            steps {
                echo "Building stage"
            }
        }
        stage ('Test') {
            steps {
                echo "Testing stage"
            }
        }
        stage ('Deploy to nginx') { 
            steps { 
                echo "Deploying" 
                script {
                    // Use AWS CLI over SSH to copy files to the Nginx server
                    sshagent(['nginx-ssh']) {
                        sh '''
                            scp -r /var/www/html/* ubuntu@18.234.215.10:/var/www/html/
                        '''
                    }
                }
            } 
        }
    }

    post {
        success {
            echo "success"
        }
        failure {
            echo "failure"
        }
    }
}
