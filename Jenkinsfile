//log what branch is being built
echo "${env.BRANCH_NAME}"

//discard builds, keep 5
properties [
    [$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5']]
]
//SHORT SYNTAX
node('dod') {
  stage 'checkout'
    checkout scm
  stage 'build'
    //build stuff
    sleep 5
}
node('dod') {
  //LONG SYNTAX
  stage name: 'test', concurrency: 3
    //test stuff concurrently, max 3 builds testing
    sleep 5
}
//only deploy if on master branch
if(env.BRANCH_NAME=="master"){
  node('dod') {
   stage name: 'deploy', concurrency: 1
     //deploy stuff one at a time
     sleep 5
     echo 'Deployed'
  }
}
