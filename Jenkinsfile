//log what branch is being built
echo "${env.BRANCH_NAME}"

//discard builds, keep 7
properties([[$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '5']]])
//SHORT SYNTAX
node('docker-cloud') {
  stage 'checkout'
    checkout scm
  stage 'build'
    //build stuff
    sleep 5
}
node('docker-cloud') {
  //LONG SYNTAX
  stage name: 'test', concurrency: 3
    //test stuff concurrently, max 3 builds testing
    sleep 5
}
//only deploy if on master branch
if(env.BRANCH_NAME=="master"){
  node('docker-cloud') {
   stage name: 'deploy', concurrency: 1
     //deploy stuff one at a time
     sleep 5
     echo 'Deployed'
  }
}
