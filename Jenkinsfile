pipeline {
  agent {
    label 'master'
  }
  environment {
    GITHUB_REPO = "$GIT_URL"
    GITHUB_COMMIT="$GIT_COMMIT"
      }

  stages {
    stage("Lint") {
      steps {
        sh env.GITHUB_REPO
      }
    }
    stage("Build CVE job"){
      steps {
        build job: 'run_docker_image_cve_scan'
  }
    }
} 
}
