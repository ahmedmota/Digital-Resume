pipeline{
    agent any 
    
    stages {
        stage ('Build'){
            steps {
                echo "Building stage"
            }
        }
        stage ('Test'){
            steps {
                echo "Testing stage"

            }
        }
        stage ('Deploy to nginx'){ 
            steps{ 
                echo "Deploying" 
                 // SSH to Nginx server and copy files to the appropriate directory
                    sshagent(['nginx-ssh']) {
                        sh "scp -r /var/www/html/* ubuntu@18.234.215.10:/var/www/html/"

					}
            } 
        }

    }

    post{
        success {
            echo "success"
        }
        failure {
            echo "failure"
        }
    }
}
