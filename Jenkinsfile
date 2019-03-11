pipeline {
    agent  { label 'master' }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                
            }
        }
        stage('DeployToStaging') {
            when {
                branch 'master'
            }
            steps {
                echo 'Testing..'
                sh 'mkdir -p /tmp/llll'                  
                
            }
        }
        stage('Deploy') {
            node('staging') {
            
              steps {
                 echo 'Deploying....'
                  sh 'mkdir -p /tmp/lllsl'
              }
            }  
        }
    }
}
