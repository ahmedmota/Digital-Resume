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
                sshagent(['nginx-ssh-1']) {
                    sh """
                    # Copy files to Nginx document root
                    scp -r * ubuntu@54.144.66.178:/var/www/html

                    # Connect to server and reload Nginx
                    ssh -t ubuntu@54.144.66.178 service nginx reload
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
