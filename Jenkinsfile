pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/Maxi-F/spring-boot-jpetstore'
        timeout(activity: true, unit: 'DAYS', time: 1) {
          withGradle() {
            sh '''
./gradlew init
./gradlew build
./gradlew jar'''
          }

        }

      }
    }

    stage('Test') {
      steps {
        timeout(unit: 'DAYS', time: 1, activity: true) {
          sh './gradlew test'
        }

      }
    }

    stage('Validate') {
      steps {
        sh 'echo validate'
      }
    }

    stage('Deploy') {
      steps {
        sh '''./gradlew bootRun --args=\'--server.port=8081\' &'''
      }
    }

  }
}
