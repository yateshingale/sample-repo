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
            subject: "SUCCESS: Job '${env.JOB_NAME} [#${env.BUILD_NUMBER}]'",
            body: """
                Good news!

                Job: ${env.JOB_NAME}
                Build: #${env.BUILD_NUMBER}
                URL: ${env.BUILD_URL}

                The build was successful!
            """,
            to: 'yateshingale03@gmail.com'
        )
    }

    failure {
        emailext(
            subject: "FAILURE: Job '${env.JOB_NAME} [#${env.BUILD_NUMBER}]'",
            body: """
                Oh no!

                Job: ${env.JOB_NAME}
                Build: #${env.BUILD_NUMBER}
                URL: ${env.BUILD_URL}

                The build failed.
            """,
            to: 'yateshingale03@gmail.com'
        )
    }
}

