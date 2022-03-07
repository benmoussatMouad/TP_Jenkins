pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './gradlew build'
      }
    }

    stage('Mail Notification') {
      steps {
        mail(subject: 'Build Succeded', body: 'The build has succeeded', to: 'hm_benmoussat@esi.dz')
      }
    }

  }
}