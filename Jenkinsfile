
pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
        timeout(time: 30, unit: 'MINUTES')
    }

    parameters {
        booleanParam(
            name: 'RUN_APP',
            defaultValue: true,
            description: 'Run the application'
        )
    }

    stages {
        stage('Checkout') {
            steps {
                deleteDir()
                checkout scm
            }
        }

        stage('Verify') {
            steps {
                echo 'Starting verification...'
                sh 'git rev-parse --short HEAD'
                sh 'test -f Jenkinsfile'
                echo 'Verification successful!'
            }
        }

        stage('Run App') {
            when {
                expression { params.RUN_APP }
            }
            steps {
                echo 'RUN_APP is enabled'
                echo 'Add your application commands here'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished'
        }
    }
}
