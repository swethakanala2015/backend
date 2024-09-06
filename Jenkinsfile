pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    stages {
        stage('read the version')
        steps{
            script{
            def packagejson = readJSON file: 'package.json'
            def appVersion = packageJson.version
            echo "application version: $appversion"
            }
        }
        stage('Install Dependencies') {
           steps {
              sh """
              npm install
              ls -ltr
              echo "application version: $appversion"
              """
        }
    }
}

      
post { 
    always { 
        echo 'I will always say Hello again!'
        deleteDir()
        }
        success { 
            echo 'I will run when pipeline is success'
        }
        failure { 
            echo 'I will run when pipeline is failure'
        }
    }
}
