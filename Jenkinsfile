pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'eu-north-1'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/JEJJAYLASAIKUMAR1208/aws-cloudformation-enterprise.git'
            }
        }

        stage('Validate CloudFormation') {
            steps {
                sh '''
                aws cloudformation validate-template \
                  --template-body file://cloudformation/storage/s3.yaml
                '''
            }
        }

        stage('Deploy Stack') {
            steps {
                sh '''
                aws cloudformation deploy \
                  --template-file cloudformation/storage/s3.yaml \
                  --stack-name nike-storage \
                  --capabilities CAPABILITY_NAMED_IAM
                '''
            }
        }
    }
}
