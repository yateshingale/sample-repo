pipeline {
    agent any

    parameters {
        string(name: 'BRANCH', defaultValue: 'master', description: 'Git branch to build')
        choice(name: 'ENV', choices: ['dev', 'qa', 'prod'], description: 'Deployment environment')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run test cases?')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${BRANCH}", url: 'https://github.com/yateshingale/sample-repo'
            }
        }

        stage('Info') {
            steps {
                echo "Building branch: ${BRANCH}"
                echo "Deploying to: ${ENV}"
                echo "Run Tests: ${RUN_TESTS}"
            }
        }

        stage('Test') {
            when {
                expression { return RUN_TESTS }
            }
            steps {
                sh 'echo "Running tests..."'
                sh 'ls -al'
                // Add your actual test command here
            }
        }
    }
}
