pipeline {
  agent {
    label 'master'
  }
  environment {
    GOPATH = "$WORKSPACE"
    GITHUB_REPO = "$GIT_URL"
    GITHUB_COMMIT="$GIT_COMMIT"
      }
 

  stages {
    stage("Lint") {
      steps {
        sh "pwd"
        sh "ls -Alh"
        sh "cut -f '2' -d '/' ${env.GITHUB_REPO}"
        sh env.GITHUB_COMMIT
      }
    }
    stage("Build CVE job"){
      steps {
        build job: 'run_docker_image_cve_scan', parameters: [[$class: 'StringParameterValue', name: 'COMMIT_ID', value: params.COMMIT_ID]]
  }
    }
} 
}
