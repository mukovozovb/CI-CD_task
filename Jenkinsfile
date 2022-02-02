pipeline {
    agent {
        label 'linux-node'
    }
    stages {
        stage('Test') {
            steps {
                sh 'echo Kekus'
                sh 'ls -l'
            }
        }
        stage('Build') {
            teps {
                sh 'chmod +x mvnw'
                sh './mvnw package -Dcheckstyle.skip'
            }
        }    
        stage('Test-Static') {
            steps {
                sh 'whoami'
                sh 'ip a'
                sh 'chmod +x mvnw'
                sh './mvnw package -Dcheckstyle.skip'
                sh 'docker build -f ./Dockerfile -t spring/petclinic .'
                sh 'docker run -d --name petclinic -p 3000:8080 spring/petclinic'
            }
        }        
    }
}
