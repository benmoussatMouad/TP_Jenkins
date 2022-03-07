pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'gradle build'
      }
    }

    stage('Mail Notification') {
      steps {
        mail(subject: 'Build Succeded', body: 'The build has succeeded', to: 'hm_benmoussat@esi.dz')
      }
    }

  }
}