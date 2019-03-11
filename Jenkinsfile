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
                script {
                    app = docker.build("willbla/train-schedule")
                    app.inside {
                        sh 'echo $(curl localhost:8082)'
                    }
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
