pipeline {
    agent {
        label 'linux-node'
    }
    stages {
        stage('linting') {
            steps {
                sh 'chmod +x linter.sh'                
                sh './linter.sh Dockerfile'          
            }
        }
   }          
}
