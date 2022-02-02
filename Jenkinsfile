pipeline {
    agent {
        label 'linux-node'
    }
    stages {
        stage('Test') {
            steps {
                sh 'ls -la'
            }
        }
        stage('Test-Static') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw package -Dcheckstyle.skip'
                sh 'sudo docker build -f ./Dockerfile -t spring/petclinic .'
                sh 'sudo docker run -d --name petclinic -p 3000:8080 spring/petclinic'
            }
        }        
    }
}
