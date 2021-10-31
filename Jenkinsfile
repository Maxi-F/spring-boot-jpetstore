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

    stage('Analyze') {
      steps {
        withGradle() {
          sh './gradlew sonarqube -Dsonar.projectKey=test -Dsonar.host.url=sonarqube:9000 -Dsonar.login=86c160c348f62303f6f89efc71d3c36ce84193ad'
        }

      }
    }

  }
}