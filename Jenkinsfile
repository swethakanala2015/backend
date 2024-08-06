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
   

    parameters {
       choice(name: 'action', choices: ['Apply', 'Destroy'], description: 'Pick something')

    }
}


    stages {
        stage('init') { 
            steps {
                sh """
                cd 01-vpc
                terraform init -reconfigure
                """
            }
        }
        stage('plan') { 
            when{
                expression {
                    params.action == 'Apply'
                }
            }
            steps {
                sh 'echo This is Test'
                sh 'sleep 10'
            }
        }
        stage('Destroy') { 
              when{
                expression {
                    params.action == 'Destroy'
                }
                steps {
                sh """
                cd 01-vpc
                terraform destroy -auto-approve
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
