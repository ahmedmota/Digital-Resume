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
            sh 'ssh-keygen -R 35.172.186.180'
            sshagent(['nginx-ssh']) {
                sh """
                # Copy files to Nginx document root
                scp -r * ubuntu@35.172.186.180:/var/www/html

                # Connect to server and reload Nginx
                ssh -t ubuntu@35.172.186.180 service nginx reload
                """
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
