pipeline {
  agent any

  environment {
    // Specify SonarQube server configuration name
    SONARQUBE_SERVER = 'SonarQube'
  }

  stages {
    stage('Checkout') {
      steps {
        // Clone the GitHub repository
        git 'https://github.com/ridha0595/jenkins-sonarqube-1.git'
      }
    }

    stage('Build') {
      steps {
        script {
          // Install Node.js dependencies
          sh 'npm install'
        }
      }
    }

    stage('SonarQube Analysis') {
      steps {
        script {
          // Run SonarQube analysis
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
