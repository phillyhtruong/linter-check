#!groovy
// Multibranch Pipeline with defaults
// Manage Jenkins > Managed files > Add a new Config > Groovy file

node() {

  environment {
    AWS_DEFAULT_REGION = 'us-east-1'
    HOME = '.'
  }
  currentBuild.result = "SUCCESS"

  print "Starting Jenkins task!"

  try {
    stage('Checkout') {
      checkout scm
    }

    stage('Test') {
      print "Start runing tests..."
      "${sh(script:'sh ./scripts/run-tests.sh', returnStdout: true)}"
    }

    stage('Cleanup') {
      echo 'prune and cleanup'
    }

  } catch (err) {
    currentBuild.result = "FAILURE"
    throw err
  }
}