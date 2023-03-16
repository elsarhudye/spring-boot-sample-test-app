pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Print message'
        sh 'mvn -DskipTests clean package'
        archiveArtifacts '**/target/*.jar'
      }
    }

    stage('test') {
      parallel {
        stage('smoke') {
          steps {
            echo 'test d\'integration'
            sh 'mvn -Dtest="com.example.testingweb.smoke.**" test'
            junit '**/target/surefire-reports/TEST-*.xml'
          }
        }

        stage('test intégration ') {
          steps {
            echo 'test fonctionnel '
            sh '''mvn -Dtest="com.example.testingweb.integration.**" test
'''
          }
        }

        stage('fonctionnel') {
          steps {
            echo 'smoke test'
            sh '''mvn -Dtest="com.example.testingweb.functional.**" test
'''
          }
        }

      }
    }

    stage('deploy') {
      steps {
        input(message: 'Voulez-vous continuer?', ok: 'Alons-y')
        echo 'deploy'
        sh '''mvn -DskipTests install
'''
      }
    }

  }
}