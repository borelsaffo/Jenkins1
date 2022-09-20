Jenkinsfile (Declarative Pipeline)
pipeline {
    agent {
        docker { image 'node:16.13.1-alpine' }
    }
   
    environment {
        IMAGE_NAME = "alpinehelloworld"
        IMAGE_TAG  = "latest"
    }
  
    stages {
        stage('Build') { 
            steps { 

                sh 'git clone https://github.com/borelsaffo/alpinehelloworld.git'
                sh 'cd alpinehelloworld' 
                sh 'doker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
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
