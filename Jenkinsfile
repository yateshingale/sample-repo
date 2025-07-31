pipeline {
    agent any

    environment {
        RECIPIENT = 'yateshingale03@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add build logic
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                // Add test logic
            }
        }
    }

    post {
        success {
            emailext(
                subject: "SUCCESS: Job '${env.JOB_NAME} [#${env.BUILD_NUMBER}]'",
                body: """<p><b>Good news!</b></p>
                         <p>Job: ${env.JOB_NAME}<br/>
                         Build: #${env.BUILD_NUMBER}<br/>
                         URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                         <p>The build was successful!</p>""",
                mimeType: 'text/html',
                to: "${env.RECIPIENT}"
            )
        }

        failure {
            emailext(
                subject: "FAILURE: Job '${env.JOB_NAME} [#${env.BUILD_NUMBER}]'",
                body: """<p><b>Build Failed!</b></p>
                         <p>Job: ${env.JOB_NAME}<br/>
                         Build: #${env.BUILD_NUMBER}<br/>
                         URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                         <p>Please check the console output for details.</p>""",
                mimeType: 'text/html',
                to: "${env.RECIPIENT}"
            )
        }
    }
}
