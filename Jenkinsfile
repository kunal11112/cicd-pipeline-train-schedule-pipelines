pipeline {
  agent any
  stages {
    stage ('Build') {
      steps {
        echo 'Running build automation'
        sh '/opt/gradle/gradle-7.2/bin/gradle --no-daemon'
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
