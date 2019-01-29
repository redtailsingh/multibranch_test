pipeline {
  agent any
  parameters {
    choice(name: 'ENVIORNMENTS',
        choices: '''
		gr_development\n
		gr_staging\n
		gr_production_api\n
		gr_patner_one\n
		gr_speak_mobile
	''',
        description: 'select an env')
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('checkout SCM') {
        steps {
            git branch: "${params.BRANCH}", url: 'https://github.com/redtailsingh/multibranch_test.git'
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
