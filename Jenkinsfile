pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './mvnw clean install'
      }
    }
    stage('Test') {
      steps {
        sh './mvnw test'
      }
    }
    stage('Package') {
      steps {
        sh './mvnw package'
      }
    }
    stage('Deploy') {
      when {
  			branch 'master'
  		}
      steps {
        sh './mvnw deploy'
        slackSend(color: 'good',
                  message: "${currentBuild.fullDisplayName} build was successful!")
        }
    }
  }
}
