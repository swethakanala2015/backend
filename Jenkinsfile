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
        stage('read the version')
           steps{
            def package.json = readJSON file: 'package.json'
            def appVersion = packageJson.version
           }
        stage('Install Depedencies') {
            steps {
                sh """
                npm install
                ls -ltr
                echo $appversion
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
}
