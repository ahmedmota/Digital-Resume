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
        script {
            sshagent(['nginx-ssh']) {
               // Copy files to the remote server (scp)
                        sh 'scp -o StrictHostKeyChecking=no -i /var/lib/jenkins/.ssh/known_hosts -r * ubuntu@54.85.198.104:/var/www/html'

                        // Connect to server and reload Nginx (ssh)
                        sh 'ssh -o StrictHostKeyChecking=no -i /var/lib/jenkins/.ssh/known_hosts -t ubuntu@54.85.198.104 service nginx reload'
            }
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
