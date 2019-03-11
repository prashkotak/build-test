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
                sh 'docker pull httpd'                  
                
            }
        }
        stage('Deploy') {
            agent {
                label 'prod'
            }
            steps {
                 echo 'Deploying....'
                  sh 'mkdir -p /tmp/lllswwl'
             }
        }
    }
}
