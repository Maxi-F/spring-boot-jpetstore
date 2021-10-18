pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/Maxi-F/spring-boot-jpetstore'
        withGradle() {
          sh '''gradle init
gradle build'''
        }

      }
    }

    stage('Test') {
      steps {
        sh 'echo test'
      }
    }

    stage('Validate') {
      steps {
        sh 'echo validate'
      }
    }

    stage('Deploy') {
      steps {
        sh 'echo deploy'
      }
    }

  }
}