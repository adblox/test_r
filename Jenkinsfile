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
        echo env.GITHUB_REPO
        echo "sh cut -d '/' -f 2 'env.GITHUB_COMMIT'"
      }
    }
    stage("Build CVE job"){
      steps {
        build job: 'run_docker_image_cve_scan', parameters: [[$class: 'StringParameterValue', name: 'upstream_commit_id', value: env.GITHUB_COMMIT]]
  }
    }
} 
}
