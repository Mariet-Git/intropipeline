pipeline {
  agent any
  stages {
    stage('corriendo en paralelo') {
      parallel {
        stage('a') {
          steps {
            echo 'Test en paralelo en linux'
          }
        }

        stage('b') {
          steps {
            echo 'Test en paralelo en windows'
          }
        }

      }
    }

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
        sh 'pwd'
        sh 'chmod +xr ./miscript.sh'
        sh './miscript.sh'
      }
    }

    stage('test: funtional') {
      when {
        branch 'test'
      }
      steps {
        sh 'echo "Ejecucion de test: funcional en rama test"'
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
        echo "User: ${username} dijo que OK."
      }
    }

  }
  environment {
    OUTPUT_PATH = './tmp'
  }
  post {
    aborted {
      echo 'No termino de correr el pipeline fue forzado a terminar'
    }

    always {
      echo 'El Pipeline se ejecuto exitosamente'
    }

    failure {
      mail(to: 'pinapinamariet@gmail.com', subject: 'Ocurrio un error en el pipeline', body: 'cuerpo del correo')
    }

  }
}