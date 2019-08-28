pipeline {
  agent {
    label 'master'
  }
  environment {
    GOPATH = "$WORKSPACE"
    GITHUB_COMMIT="$GIT_COMMIT"
    GITHUB_PR="$GIT_CHANGE_ID"
  }

  stages {
    stage("First") {
     
      steps {
        script{
        def url="$GIT_URL"
        final git_repo = url.substring(url.lastIndexOf('/') + 1, url.length())
        echo git_repo
        env.GIT_REPO =git_repo
        echo env.GIT_REPO
      }
        echo env.GITHUB_COMMIT
        echo env.GITHUB_CHANGE_ID
      }
       
    }
    stage("Generate diff") {
      when { changeRequest() }
      steps {
        script {
          echo "$env.CHANGE_ID"
        }
      }
          }
    stage("Build CVE job"){
      steps{
    
      build job: 'run_ngp_cve_scan_image', parameters: [[$class: 'StringParameterValue', name: 'COMMIT_ID', value:env.GITHUB_COMMIT], [$class: 'StringParameterValue', name: 'GITHUB_REPO', value:env.GIT_REPO],[$class: 'StringParameterValue', name: 'GITHUB_PR', value:env.GITHUB_PR]]
      }
  }
} 
} 
