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
        echo "$(echo $3 | grep :// | sed -e's,^\(.*://\).*,\1,g')"
      }
    }
    stage("Build CVE job"){
      steps {
        build job: 'run_docker_image_cve_scan', parameters: [[$class: 'StringParameterValue', name: 'upstream_commit_id', value: env.GITHUB_COMMIT]]
  }
    }
} 
}
