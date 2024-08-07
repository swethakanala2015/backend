pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansicolor('xterm')
    }
     parameters {
        choice(name: 'action', choices: ['Apply', 'Destroy'], description: 'Pick something')
    }    
    stages {
        stage('test') {
            steps {
                sh """
                echo "this is testing"
                """
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
