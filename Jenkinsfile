pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'echo Building...'
                // Uncomment below line to simulate a failure
                // bat 'exit 1'
            }
        }
    }
    post {
        success {
            mail to: 'manesankett@gmail.com',
                 subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Great news, the build succeeded!\n\nDetails: ${env.BUILD_URL}"
        }
        failure {
            mail to: 'manesankett@gmail.com',
                 subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Unfortunately, the build failed.\n\nDetails: ${env.BUILD_URL}"
        }
    }
}
