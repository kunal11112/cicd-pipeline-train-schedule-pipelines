// this is declarative pipeline
CODE_CHANGES = getGitChanges()
pipeline {
  agent any // this build will run on any available agent (agent may be linux node, windows nodes, containers)
  tools {    //Access build tools for your project like maven, gradle and jdk
    maven 'Maven'
  }
  parameters {     //if we wants to select which version of application we wants to deploy for that parameter block will used
     string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
      choice(name: 'VERSION', choices: ['1.1.0', 1.2.0])
      booleanParam(name: 'executeTests', defaultValue: true, description: '')  // how to call parameter check in build stage
  }
  }
  environment {   //used to define environment variable 
     NEW_VERSION = '1.3.0'
  }
  stages {       // where the work happens 
    stage ('Build') {
        when {
        expression {
           BRANCH_NAME == 'dev' && CODE_CHANGES == true    // if we want that when code changes will be there then build stage will run
        }
        when {
          expression {
            param.executeTests    //if parameter execute test condition will true then build stage will executed else not
        }
      }
      steps {
        echo 'Running build automation'
        echo "building version ${NEW_VERSION}"
        #sh '/opt/gradle/gradle-7.2/bin/gradle --no-daemon'
        #archieveArtifacts artifacts: 'dist/trainSchedule.zip'
      }
    }
   stage ('Test') {    //suppose if we want to execute this stage for a particular branch then we can use when expression
      when {
        expression {
           BRANCH_NAME == 'dev' || BRANCH_NAME == 'master'
        }
      }
     steps {
       echo 'This is test stage'
   }
}
   stage ('Deploy') {
     steps {
       echo 'This is deploy stage'
       withCredentials([
         usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)
       ]) {
          sh "some script ${USER} ${PWD}"  // this is the way to define bind credentials in jenkins file so there are two ways either define directlt in environment block or define in with credentials wrapper for that we need to install plugins credentials and credentials bind plugin
   }
}
post {                    // we can execute some logic after all stages executed condition like always, success, failure
   always {
   }
  success {
  }
  }
}
