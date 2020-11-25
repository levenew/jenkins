def projectName = "core-dependencies"
def svnUrl = "https://172.23.2.1/svn/jpCore/new2/core-dependencies"
def credentialsId = "liw"


pipeline {
    agent any
    tools {
        maven "Maven"
    }
    stages {
        stage('Svn pull') {
            steps {
                echo "start Svn pull ${projectName}"
                checkout([$class                : 'SubversionSCM',
                          additionalCredentials : [],
                          excludedCommitMessages: '',
                          excludedRegions       : '',
                          excludedRevprop       : '',
                          excludedUsers         : '',
                          filterChangelog       : false,
                          ignoreDirPropChanges  : false,
                          includedRegions       : '',
                          locations             : [[
                                                           cancelProcessOnExternalsFail: true,
                                                           credentialsId               : "${credentialsId}",
                                                           depthOption                 : 'infinity',
                                                           ignoreExternalsOption       : true,
                                                           local                       : '.',
                                                           remote                      : "${svnUrl}"]],
                          quietOperation        : true, workspaceUpdater: [$class: 'UpdateUpdater'
                ]])
            }
        }
        stage('Maven build') {
            when { changeset "**/*.*" }
            steps {
                echo "start Maven build ${projectName}"
                sh "mvn -Dmaven.test.failure.ignore=true clean install"
            }
        }
    }
}

