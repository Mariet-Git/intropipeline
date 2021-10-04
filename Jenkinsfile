pipeline {
  agent any
  stages {
    stage('Say Hello') {
      steps {
        echo "Hello ${params.Name}!"
        echo "Hello ${MY_NAME}"
        sh 'java -version'
      }
    }

  }
  environment {
    MY_NAME = 'Mariet'
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
}