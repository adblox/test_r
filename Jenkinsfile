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
      build job: 'run_ngp_cve_scan_image', parameters: [[$class: 'StringParameterValue', name: 'COMMIT_ID', value: ${COMMIT_ID}]]
  }
} 
