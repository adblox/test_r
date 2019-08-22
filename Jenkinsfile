pipeline {
  agent {
    label 'master'
  }
  environment {
    GOPATH = "$WORKSPACE"
  }
  parameters {
    string defaultValue: '1', description: '', name: 'COMMIT_ID'
  }
  stages {
    stage("Lint") {
      steps {
        sh "pwd"
        sh "ls -Alh"
      }
    }
    stage("Build CVE job"){
      steps {
        build job: 'run_docker_image_cve_scan', parameters: [[$class: 'StringParameterValue', name: 'COMMIT_ID', value: params.COMMIT_ID]]
  }
    }
} 
}
