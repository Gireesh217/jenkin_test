pipeline {
    agent any

    environment {
        AWS_REGION = 'us-west-2' // change as needed
        S3_BUCKET = 'jenkins-practice-bucket'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Gireesh217/jenkin_test.git', branch: 'main'
            }
        }

        stage('Deploy to S3') {
            steps {
                script {
                    sh '''
                    aws s3 sync web/ s3://$S3_BUCKET/ --region $AWS_REGION --delete
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment to S3 completed successfully.'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
