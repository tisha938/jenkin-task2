pipeline {
  agent any
  
  environment {
        AWS_REGION = 'ap-south-1'
        S3_BUCKET = 'tisha-jenkin-bucket' 
        PATH = "/usr/local/bin:$PATH"
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
        AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
    }


  tools { 
    nodejs 'node' 
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/tisha938/jenkin-task2.git'
      }
    }

    stage('Build React App') {
      steps {
        sh 'ls'
        sh 'cd React-DefaultApp'
        sh 'npm install'
        sh 'npm run build'
      }
    }

    stage('Deploy to S3') {
            steps {
                sh '''
                aws s3 sync build/ s3://$S3_BUCKET/ --region $AWS_REGION
                '''
            }
  }
}}
