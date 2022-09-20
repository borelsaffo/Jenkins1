Jenkinsfile (Declarative Pipeline)
pipeline {
    agent {
        docker { image 'node:16.13.1-alpine' }
    }
    
    stages {
        stage('Build') { 
            steps { 
                sh 'make' 
            }
        }
        stage('Test'){
            steps {
                sh 'make check'
                junit 'reports/**/*.xml' 
            }
        }
        stage('artefact') {
            steps {
                sh 'make publish'
            }
        }
    }
}
