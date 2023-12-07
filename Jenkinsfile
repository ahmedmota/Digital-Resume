pipeline {
    agent any
    
    stages {
        stage('Checkout from GitHub') {
            steps {
                // Clean workspace and checkout code from GitHub repository
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/ahmedmota/Digital-Resume.git']]])
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    // SSH to Nginx server and copy files to the appropriate directory
                    sshagent(['nginx-ssh']) {
                        sh "scp -r /var/www/html/* ubuntu@18.234.215.10:/var/www/html/"
                    }
                }
            }
        }
    }
}
