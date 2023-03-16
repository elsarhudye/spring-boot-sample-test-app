pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Print message'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'test d\'integration'
          }
        }

        stage('test fonctionnel ') {
          steps {
            echo 'test fonctionnel '
          }
        }

        stage('smoke test') {
          steps {
            echo 'smoke test'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        echo 'deploy'
      }
    }

  }
}