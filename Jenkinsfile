pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'echo "Un paso sencillo de una linea"'
        sh '''
              echo "Pasos multilinea"
              cd /tmp
              ls -lrt
              '''
      }
    }

    stage('test: integration y calidad') {
      steps {
        sh 'echo "Paso de test: integracion y calidad"'
      }
    }

    stage('test: funtional') {
      steps {
        sh 'echo "Paso de test: funcional"'
      }
    }

    stage('abrobation') {
      steps {
        sh 'echo "Paso de test: aprobacion"'
      }
    }

    stage('deploy:prod') {
      steps {
        sh 'echo "Paso de test: deploy:prod"'
      }
    }

  }
}