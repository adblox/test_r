pipeline {
  agent {
    label 'master'
  }
  environment {
    GOPATH = "$WORKSPACE"
  }
  parameters {
    choice choices: ['1', '2', '3'], description: '', name: 'choice'
    password defaultValue: '1', description: '', name: 'password'
  }
  stages {
    stage("Lint") {
      steps {
        sh "pwd"
        sh "ls -Alh"
      }
    }
  }
}
