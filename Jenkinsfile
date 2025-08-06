pipeline {
  agent none

  triggers {
    githubPush()
  }

  stages {
    stage('Deploy to Test') {
      agent { label 'test' }
      when { branch 'develop' }
      steps {
        checkout scm
        sh '''
          echo "Deploying to Test Node..."
          rm -rf /home/ubuntu/jenkins/test/
          mkdir -p /home/ubuntu/jenkins/test/
          cp -R . /home/ubuntu/jenkins/test/
        '''
      }
    }

    stage('Deploy to Prod') {
      agent { label 'prod' }
      steps {
        checkout scm
        sh '''
          echo "Deploying to Prod Node..."
          rm -rf /home/ubuntu/jenkins/prod/
          mkdir -p /home/ubuntu/jenkins/prod/
          cp -R . /home/ubuntu/jenkins/prod/
        '''
      }
    }
  }

  post {
    success {
      echo '✅ Deployment successful!'
    }
    failure {
      echo '❌ Deployment failed.'
    }
  }
}
