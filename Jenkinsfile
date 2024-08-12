pipeline {
  agent any
  
  environment {
    TAG_NAME = "build_app"
    bucket = "tisha-jenkin-bucket"
    BuildDir = 'build-folder'
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
        
        sh 'npm install'
        sh 'npm run build'
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
