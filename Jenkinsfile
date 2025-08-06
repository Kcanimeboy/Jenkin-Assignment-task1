pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Run only when develop branch') {
            when {
                branch 'develop'
            }
            steps {
                echo 'Checking out develop branch'

                checkout scm

                sh 'mkdir -p pulled_files'
                sh 'cp -r * pulled_files/'

                echo 'Files copied to pulled_files directory'
            }
        }
    }
}
