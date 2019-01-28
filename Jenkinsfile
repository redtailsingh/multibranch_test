pipeline {
  agent any
  stages {
    stage('build') {
        steps {
            echo 'bundle install'
        }
    }
    stage('deploy') {
        steps {
            echo 'cap development deploy'
        }
    }
  }
}

