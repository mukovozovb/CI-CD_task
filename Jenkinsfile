pipeline {
    agent {
        label 'linux-node'
    }
    stages {
        stage('Test') {
            steps {
                
            }
        }
         stage('Linting') {
            steps {
                sh 'cd ./bin'
                sh 'chmod +x hadolint'
                sh 'cd ..'
                sh './bin/hadoint Dockerfile'
                sh 'chmod +x linter.sh && linter.sh Dockerfile'
                sh 'cat linter.sh'   
                sh 'chmod +x linter.sh'            
                dir ('/var/lib/jenkins/workspace/multibranch_docker') { 
                sh('./linter.sh Dockerfile')
                }
                sh 'linter.sh Dockerfile'
                sh './linter.sh Dockerfile'
                sh '''#!/bin/bash
                       dockerfile=Dockerfile
                       shift
                       docker run --rm -i hadolint/hadolint hadolint "$dockerfile" < $dockerfile
                '''
            }
        }
        stage('Test-Static') {
            steps {
                sh 'chmod +x mvnw'
                sh './mvnw package -Dcheckstyle.skip'
                sh 'docker build -f ./Dockerfile -t spring/petclinic .'
                sh 'docker run -d --name petclinic -p 3000:8080 spring/petclinic'
            }
        }        
    }
}
