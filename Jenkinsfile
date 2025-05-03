## this is declarative pipeline
pipeline {
  agent any   # this build will run on any available agent (agent may be linux node, windows nodes, containers)
  stages {       # where the work happens
    stage ('Build') {
      steps {
        echo 'Running build automation'
        #sh '/opt/gradle/gradle-7.2/bin/gradle --no-daemon'
        #archieveArtifacts artifacts: 'dist/trainSchedule.zip'
      }
    }
   stage ('Test') {
     steps {
       echo 'This is test stage'
   }
}
   stage ('Deploy') {
     steps {
       echo 'This is deploy stage'
   }
}
  }
}
