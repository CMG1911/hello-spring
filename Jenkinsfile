pipeline {
    agent any
    options { timestamps() 
	ansiColor('xterm')	
	}
    stages {
        stage('TestingDocker') {
		    steps {
                sh 'docker-compose config'
            }
        }
        stage('Compilación y Construcción') {
            steps {
                sh '''./mvnw package
                docker-compose build'''
            }
                post {
                        always {
                                junit 'target/surefire-reports/*.xml'
                        }
                }
        }        
	    stage('Levantamiento') {
            steps {
                       sh '''docker-compose up -d
                       docker-compose logs -t --tail=10'''
                       
		       echo '\033[1;32m[Success] \033[0m'
                }
        }
        
    }
}