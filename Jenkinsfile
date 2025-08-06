pipeline {
    agent { label 'test' }

    stages {
        stage('Checkout and Copy') {
            steps {
                // Checkout code from SCM
                checkout scm

                // Create target folder
                sh 'mkdir -p pulled_files'

                // Copy all contents to the folder
                sh 'cp -r * pulled_files/'
            }
        }
    }
}
