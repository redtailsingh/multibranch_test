pipeline {
  agent any
  parameters {
    choice(name: 'ENVIORNMENTS',
        choices: 'development\ntesting\nproduction',
        description: 'select an env')
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('checkout scm') {
        steps {
            echo "checking out ${params.BRANCH}"
            git branch: "${params.BRANCH}", url: 'https://github.com/redtailsingh/multibranch_test.git'
        }
    }
    stage('build') {
        steps {
            echo 'Doing bundle install'
        }
    }
    stage('deploy') {
        steps {
            echo "Deloying to ENV:  ${params.ENVIORNMENTS}"
            echo "cap ${params.ENVIORNMENTS} deploy -s branch=${params.BRANCH}"
        }
    }
  }
}

