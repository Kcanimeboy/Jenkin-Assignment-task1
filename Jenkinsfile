pipeline {
    agent {
        label (env.BRANCH_NAME == 'main' ? 'prod' : 'test')
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Store in Folder') {
            steps {
                echo "Copying files into pulled_files directory..."

                sh '''
                    mkdir -p pulled_files
                    cp -r * pulled_files/
                '''
            }
        }
    }
}
