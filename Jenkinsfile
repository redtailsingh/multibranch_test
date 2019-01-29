pipeline {
  agent any
  parameters {
    choice(name: 'ENVIORNMENT',
        choices: '''\
		\n
		gr_development\n
		gr_staging\n
		gr_production_api\n
		gr_patner_one\n
		gr_speak_mobile
	'''.stripIndent(),
        description: 'please select an enviornment')
    gitParameter branchFilter: 'origin/(.*)', defaultValue: '', name: 'BRANCH', type: 'PT_BRANCH'
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
	    script {
            	if (params.BRANCH && params.ENVIORNMENT) {
            		echo "cap ${params.ENVIORNMENT} deploy -s branch=${params.BRANCH}"
	    	}
	    }
        }
    }
  }
}
