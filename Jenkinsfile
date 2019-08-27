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
        sh "basename $env.GITHUB_REPO" 
        sh "repo= ${basename $env.GITHUB_REPO} && env.GITHUB_REPO=${repo} "
        echo env.GITHUB_COMMIT
      }
    }
    stage("Build CVE job"){
      steps {
        build job: 'run_docker_image_cve_scan', parameters: [[$class: 'StringParameterValue', name: 'upstream_commit_id', value: env.GITHUB_COMMIT]]
  }
    }
} 
}
