pipeline {
    agent any
    environment {
        S3_BUCKET = "nixtechnix.com-793110104712-us-east-2-an"
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/nixacetech/nixtechnix.com.git'
            }
        }
        stage('Deploy to S3') {
            steps {
                sh '''
                aws s3 sync . s3://$S3_BUCKET \
                --exclude ".git/*" \
                --delete
                '''
            }
        }
    }
}
