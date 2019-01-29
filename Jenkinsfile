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
	    sh "git branch"
            git branch: "${params.BRANCH}", url: 'https://github.com/redtailsingh/multibranch_test.git'
            sh "git branch"
        }
    }
    stage('build') {
        steps {
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

