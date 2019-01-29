pipeline {
  agent any
  parameters {
    choice(name: 'ENVIORNMENTS',
        choices: 'gr_development\ngr_staging\ngr_production_api',
        description: 'select an env')
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('Checkout branch') {
        steps {
            git branch: "${params.BRANCH}", url: 'https://github.com/redtailsingh/multibranch_test.git'
        }
    }
    stage('build') {
        steps {
            sh "rvm 2.3.0"
            sh "bundle install"
        }    
    }
    stage('deploy') {
        steps {
            echo "cap ${params.ENVIORNMENTS} deploy -s branch=${params.BRANCH}"
        }
    }
  }
}

