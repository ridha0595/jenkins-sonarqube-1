pipeline {
  agent any

  environment {
    SONARQUBE_SERVER = 'SonarQube'
  }
 tools {
    nodejs 'NodeJS 22.7.0'  // Name should match the one configured in Global Tool Configuration
  }
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/ridha0595/jenkins-sonarqube-1.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        script {
          sh 'npm install'
        }
      }
    }

    stage('Build') {
      steps {
        script {
          sh 'npm run build'
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
