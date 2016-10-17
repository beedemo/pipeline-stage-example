//log what branch is being built
echo "${env.BRANCH_NAME}"
//SHORT SYNTAX
stage('build') {
 helloWorld('Bob')
 //build stuff
 echo 'fixed'
 sleep 6
}

//LONG SYNTAX
stage('test') {
  //test stuff concurrently, max 3 builds testing
  sleep 5
}
if(env.BRANCH_NAME=="master"){
 //abort an previous run if it hasn't reached this point
 milestone 1
 stage('deploy') {
   //deploy stuff one at a time
   sleep 5
   echo 'Deployed'
   node('docker-cloud') {
     checkout scm
     sh('git rev-parse HEAD > GIT_COMMIT')
     git_commit=readFile('GIT_COMMIT')
     short_commit=git_commit.take(7)
     deployAnalytics("http://elasticsearch.jenkins.beedemo.net", "es-auth", "example cloud", "stage-example", "stage-example.jar", "na",  new Date().format("EEE, d MMM yyyy HH:mm:ss Z"), short_commit, "Success")
   }
 }
}
