pipeline {
  agent any
  parameters {
    choice(name: 'Enviornments',
        choices: 'development\ntesting\nproduction',
        description: 'select an env')
    choice(name: 'Branches',
        choices: 'branch1\nbranch2\nbranch3',
        description: 'select the branch')
  }
  stages {
    stage('build') {
        steps {
            echo "select a branch ${params.Branches}"
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

