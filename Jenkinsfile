pipeline {
  agent any
  stages {
    stage('Svn pull') {
      steps {
        tool(name: 'maven', type: 'Maven')
        echo 'start Svn pull ${projectName}'
      }
    }

  }
  environment {
    projectName = 'core-support'
  }
}