//log what branch is being built
echo "${env.BRANCH_NAME}"
//SHORT SYNTAX
stage('build') {
 helloWorld('Bob')
 //build stuff
 echo 'fixed'
 sleep 6
}

milestone 1
stage('test') {
  //lock the selenium agents
  lock(inversePrecedence: true, resource: 'selenium-firefox') {
    input message: 'Do you want to execute the Selenium tests?', ok: 'Yes', submitter: 'cloudbees_admins'
    milestone 2
    node('selenium-firefox') {
      sh 'java -version'    
    }
  }
}
if(env.BRANCH_NAME=="master"){
 //abort an previous run if it hasn't reached this point
 milestone 3
 stage('deploy') {
   input message: 'Do you want to deploy to production?', ok: 'Yes', submitter: 'cloudbees_admins'
   //deploy stuff one at a time
   sleep 5
   echo 'Deployed'
   node('docker-cloud') {
     checkout scm
     sh('git rev-parse HEAD > GIT_COMMIT')
     git_commit=readFile('GIT_COMMIT')
     short_commit=git_commit.take(7)
     deployAnalytics("http://elasticsearch.jenkins.beedemo.net", "es-auth", "docker-swarm", "stage-example", "stage-example.jar", "na",  new Date().format("EEE, d MMM yyyy HH:mm:ss Z"), short_commit, "Success")
   }
 }
}
