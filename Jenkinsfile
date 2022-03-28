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

    stage('Code Analyse') {
      parallel {
        stage('Code Analyse') {
          steps {
            withSonarQubeEnv('sonar') {
              waitForQualityGate true
            }

          }
        }

        stage('Test Report') {
          steps {
            sh './gradlew test'
          }
        }

      }
    }

    stage('deployment') {
      steps {
        sh './gradlew publish'
      }
    }

    stage('Slack Notification') {
      steps {
        slackSend(attachments: 'Hello worldts', blocks: 'hello world', baseUrl: 'https://hooks.slack.com/services/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')
      }
    }

  }
}