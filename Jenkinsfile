properties([[$class: 'BuildDiscarderProperty', strategy: [$class: 'LogRotator', artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5']]])
//log what branch is being built
echo "${env.BRANCH_NAME}"
//SHORT SYNTAX
stage 'build'
 //build stuff
 sleep 5

//LONG SYNTAX
stage name: 'test', concurrency: 3
  //test stuff concurrently, max 3 builds testing
  sleep 5
if(env.BRANCH_NAME=="master"){
  stage name: 'deploy', concurrency: 1
    //deploy stuff one at a time
    sleep 5
    echo 'Deployed'
}
