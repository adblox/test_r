pipeline {
  agent {
    label 'master'
  }
  environment {
    GOPATH = "$WORKSPACE"
    GITHUB_REPO = "$GIT_URL"
      }
 
  parameters {
    string defaultValue: '${COMMIT_ID}', description: '', name: 'COMMIT_ID'
  }
  stages {
    stage("Lint") {
      steps {
        sh "pwd"
        sh "ls -Alh"
        sh env.GITHUB_REPO
      }
    }
    stage("Build CVE job"){
      steps {
        build job: 'run_docker_image_cve_scan', parameters: [[$class: 'StringParameterValue', name: 'COMMIT_ID', value: params.COMMIT_ID]]
  }
    }
} 
}
