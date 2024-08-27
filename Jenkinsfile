pipeline {
  agent any

  environment {
    // Specify SonarQube server configuration name
    SONARQUBE_SERVER = 'SonarQube'
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/your-repo/nodejs-sample-app.git'
      }
    }

    stage('Build') {
      steps {
        script {
          sh 'npm install'
        }
      }
    }

    stage('SonarQube Analysis') {
      steps {
        script {
          withSonarQubeEnv(SONARQUBE_SERVER) {
            sh 'sonar-scanner'
          }
        }
      }
    }

    stage('Deploy') {
      steps {
        script {
          // Add your deployment steps here
          echo 'Deploying to test environment...'
        }
      }
    }
  }

  post {
    success {
      echo 'Build, analysis, and deployment completed successfully!'
    }
    failure {
      echo 'Build or analysis failed.'
    }
  }
}
