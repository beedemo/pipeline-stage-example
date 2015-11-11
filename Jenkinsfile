//SHORT SYNTAX
stage 'build'
 //build stuff
 sleep 10

//LONG SYNTAX
stage name: 'test', concurrency: 3
  //test stuff concurrently, max 3 builds testing
  sleep 15

stage name: 'deploy', concurrency: 1
  //deploy stuff one at a time
  sleep 10
  echo 'simple update'
