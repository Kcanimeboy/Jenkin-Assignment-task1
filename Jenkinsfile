pipeline {
    agent none

    triggers {
        githubPush()
    }

    stages {
        stage('Deploy to Test') {
            when {
                branch 'develop'
            }
            agent { label 'test' }
            steps {
                echo "Deploying to Test Node..."
                sh '''
                    rm -rf /home/ubuntu/jenkins/test/
                    mkdir -p /home/ubuntu/jenkins/test/
                    cp -R * /home/ubuntu/jenkins/test/
                '''
            }
        }

        stage('Deploy to Prod') {
            when {
                branch 'develop'
            }
            agent { label 'prod' }
            steps {
                echo "Deploying to Prod Node..."
                sh '''
                    rm -rf /home/ubuntu/jenkins/prod/
                    mkdir -p /home/ubuntu/jenkins/prod/
                    cp -R * /home/ubuntu/jenkins/prod/
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
