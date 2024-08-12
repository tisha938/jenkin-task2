pipeline {
  agent any
  
  environment {
    TAG_NAME = "build_app"
    bucket = "tisha-jenkin-bucket"
    BuildDir = 'build'
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
        dir('/Users/macbookpro/code/jenkin/task2/React-DefaultApp')
       { sh 'npm install'
        sh 'npm run build'}
      }
    }

    stage('Upload to S3') {
      steps {
        s3Upload(
          bucket: "${bucket}", 
          path: "react-app", 
          file: "${BuildDir}/**/*", 
          acl: 'public-read'
        )
      }
    }
  }
}
