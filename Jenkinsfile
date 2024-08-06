 pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
                // Timeout counter starts BEFORE agent is allocated
                timeout(time: 30, unit: 'MINUTES')
                disableConcurrentBuilds()
                ansicolor('xterm')

    }
   
}


    stages {
        stage('test') { 
            steps {
                sh """
                cd 01-vpc
                terraform init -reconfigure
                """
            }
        }
 
    
  }
  post {
    always{
        echo 'I will always say hello again!'
        deleteDir()
    }
    success{
        echo'I will run when pipeline is success!'
    }
    failure{
        echo'I will run when pipeline is failure!'
    }
  }
