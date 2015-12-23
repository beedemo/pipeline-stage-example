//log what branch is being built
echo "${env.BRANCH_NAME}"
//SHORT SYNTAX
node('dod') {
  stage 'checkout'
    //checkout scm
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
if(env.BRANCH_NAME=="master"){
node('dod') {
   stage name: 'deploy', concurrency: 1
     //deploy stuff one at a time
     sleep 5
     echo 'Deployed'
  }
}
