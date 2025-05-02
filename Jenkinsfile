pipeline {
  agent any
  stages {
    stage ('Build') {
      steps {
        echo 'Running build automation'
        sh './gradlew --gradle-version=7.3 build --no-daemon'
        archieveArtifacts artifacts: 'dist/trainSchedule.zip'
      }
    }
   stage ('Test') {
     steps {
       echo 'This is test stage'
   }
}
  }
}
