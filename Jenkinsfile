node {
  /* checkout scm */

  /* Pull docker container from ECR */
  docker.withRegistry('https://225195660222.dkr.ecr.us-east-1.amazonaws.com/fugue/client', 'ecr:us-east-1:ecsrepo' ) {
    docker.image('225195660222.dkr.ecr.us-east-1.amazonaws.com/fugue/client:latest').inside {
      sh 'fugue --version'
      sh 'cat Policy.lw'
      sh 'lwc Policy.lw'
    }
  }
}
