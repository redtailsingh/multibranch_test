pipeline {
  agent any
  parameters {
    choice(name: 'Enviornments',
        choices: 'development\ntesting\nproduction',
        description: 'select an env')
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('build') {
        steps {
            git branch: "${params.BRANCH}", url: 'https://github.com/redtailsingh/multibranch_test.git'
            echo 'Doing bundle install'
        }
    }
    stage('deploy') {
        steps {
            echo "elect an ENV ${params.Enviornments}"
            echo "cap ${params.Enviornments} deploy -s branch=${params.Branches}"
        }
    }
  }
}
