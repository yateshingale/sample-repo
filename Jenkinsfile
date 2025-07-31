pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // your build logic here
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                // your test logic here
            }
        }
    }

    post {
        success {
            emailext(
                subject: 'SUCCESS: Job ${env.JOB_NAME} Build #${env.BUILD_NUMBER}',
                body: 'Good news! The build was successful.\n\nCheck it here: ${env.BUILD_URL}',
                to: 'yateshingale03@gmail.com'
            )
        }

        failure {
            emailext(
                subject: 'FAILURE: Job ${env.JOB_NAME} Build #${env.BUILD_NUMBER}',
                body: 'Oops! The build failed.\n\nCheck it here: ${env.BUILD_URL}',
                to: 'yateshingale03@gmail.com'
            )
        }
    }
}
