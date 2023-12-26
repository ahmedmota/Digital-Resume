pipeline{
    agent any 
    environment {
    AWS_DEFAULT_REGION = "us-east-1"
    THE_BUTLER_SAYS_SO = credentials('aws')
    }
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
        stage ('Deploy to S3'){ 
            steps{ 
                echo "Deploying" 
             sh '/root/.aws/s3 sync ./ s3://ahmedresume.online --exclude "*" --include "index.html"'

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
