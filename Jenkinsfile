pipeline {
  agent any
  stages {
    stage('Step1') {
      parallel {
        stage('Step1') {
          steps {
            echo 'step1'
          }
        }

        stage('step2') {
          steps {
            echo 'Step2'
          }
        }

      }
    }

  }
  environment {
    projectName = 'core-support'
  }
}