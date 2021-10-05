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
      input {
        message 'Presiona OK para continuar'
        submitter 'user1, user2'
        parameters {
          string(name: 'username', defaultValue: 'user', description: 'Nombre de usuario que esta dando OK')
        }
      }
      steps {
        sh 'echo "Paso de test: deploy:prod"'
        echo "User: ${params.username} dijo que OK."
      }
    }

  }
  environment {
    OUTPUT_PATH = './tmp'
  }
}