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
                    app = docker.build("prashkotak/build-test")
                    sh 'docker run -dit --name my-running-app -p 8082:80 docker.io/httpd' 		
                }
			}				
        }
		stage('DockerPush') {
			when {
                branch 'master'
            }
			steps {
				script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-login') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
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
