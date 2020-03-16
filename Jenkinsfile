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
      steps {
        sh './mvnw deploy -DaltDeploymentRepository=internal.repo::default::file:///Users/andyvu⁩/⁨Downloads⁩/SOEN345⁩/⁨Assignments⁩/Assignment6⁩/⁨PetClinic/spring-petclinic/Jenkins'
        slackSend(color: 'good',
                  message: "${currentBuild.fullDisplayName} build was successful!")
        }
    }
  }
}
