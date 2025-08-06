pipeline {
  agent { label 'prod' }
  stages {
    stage('Checkout and Copy') {
      steps {
        checkout scm

        sh '''
          # make sure we're starting clean
          rm -rf pulled_files
          mkdir -p pulled_files

          # sync everything except the staging dir itself
          rsync -av --exclude='pulled_files' ./ pulled_files/
        '''
      }
    }
  }
}
