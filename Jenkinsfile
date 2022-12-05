pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('cloning') {
            steps {
                git branch: 'main', url: 'https://github.com/SergioJimenez98/laboratorio4-usipMod8.git'
            }
        }
        
        stage('Build') { 
            steps { 
                sh "docker-compose up"
                //sh 'make' 
            }
        }
        stage('Test'){
            steps {
                sh 'make check'
                junit 'reports/**/*.xml' 
            }
        }
        stage('Deploy') {
            steps {
                sh 'make publish'
            }
        }
    }
}
