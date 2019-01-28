pipeline {
  agent any
  parameters {
    choice(name: 'Enviornments',
        choices: 'development\ntesting\nproduction',
        description: 'select an env')
    choice(name: 'Branches',
        choices: 'branch1\nbranch2\nbranch3',
        description: 'select the branch')
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('build') {
        steps {
            echo "select a branch ${params.Branches}"
            git branch: "${params.BRANCH}", url: 'https://github.com/redtailsingh/multibranch_test.git'
            echo "git checkout ${params.Branches}"
            echo "bundle install"
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

