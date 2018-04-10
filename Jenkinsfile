node {

  /* Setup our environment */
  withEnv(["AWS_DEFAULT_REGION=us-east-1",
           "FUGUE_RBAC_DO_AS=1",
           "FUGUE_LWC_OPTIONS=true"]) {

    /* Checkout git repo */
    checkout(scm)

    /* Use Amazon ECR repo */
    docker.withRegistry("https://721018433921.dkr.ecr.us-east-1.amazonaws.com/fugue/client", "ecr:us-east-1:ECS_REPO" ) {

      /* Pull the fugue client docker container from ECR */
      docker.image("721018433921.dkr.ecr.us-east-1.amazonaws.com/fugue/client").inside {

        /* Set our Fugue credentials */
        withCredentials([string(credentialsId: "FUGUE_USER_NAME", variable: "FUGUE_USER_NAME"),
                         string(credentialsId: "FUGUE_USER_SECRET", variable: "FUGUE_USER_SECRET")]) {

          /* Validate that the policy compiles */
          stage("Validate Policy") {
            sh(script: "lwc Policy.lw")
          }

          /* Apply policy to the Fugue Conductor */
          stage("Apply Policy") {
            sh(script: "fugue policy rbac-attach Policy.lw")
          }
        }
      }
    }
  }
}
