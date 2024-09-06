pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    stages  {
        stage('Install Dependencies') {
           steps {
             sh """
             npm install
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
