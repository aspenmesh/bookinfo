node('docker') {
  properties([disableConcurrentBuilds()])

  repository = "quay.io/aspenmesh/bookinfo-private"
  version = "${env.BRANCH_NAME}-${env.BUILD_ID}"

  stage('Checkout') {
    checkout scm
  }

  stage('Build and Push') {
    docker.withRegistry('https://quay.io', 'quay-infrajenkins-robot-creds') {
      sh "./build_push_update_images.sh $repository $version"
    }
  }
}
