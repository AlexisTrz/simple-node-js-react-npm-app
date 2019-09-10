pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'True'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage ('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage ('deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'finished using the website? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
