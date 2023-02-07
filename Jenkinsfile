pipeline {
    agent any
    options { timestamps() 
	ansiColor('xterm')	
	}
    stages {
        stage('Compilación') {
            steps {
                sh './mvnw package'
            }
        }    
        stage('Construcción') {
            steps {
                sh 'docker-compose build'
            }
        }
        stage('Levantamiento') {
            steps {
                sh 'docker-compose up -d docker-compose logs -t --tail=10'
                echo '\033[1;32m[Success] \033[0m'
            }
        }
    
    }
}
