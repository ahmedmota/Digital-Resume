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
        stage('Deploy') {
            steps {
                sshagent(['nginx-ssh']) {
                    sh """
                    # Copy files to Nginx document root
                    scp -r * ubuntu@18.234.215.10:/var/www/html

                    # Connect to server and reload Nginx
                    ssh -t ubuntu@18.234.215.10 service nginx reload
                    """
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
