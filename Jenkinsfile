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
                // Clone your repo
                git url: 'https://github.com/yateshingale/sample-repo', branch: "${params.BRANCH}"
                
                // OR if repo already cloned, just checkout
                sh "git checkout ${params.BRANCH}"
            }
        }

        stage('Info') {
            steps {
                echo "Building branch: ${params.BRANCH}"
                echo "Deploying to: ${params.ENV}"
                echo "Run Tests: ${params.RUN_TESTS}"
            }
        }

        stage('Test') {
            steps {
                script {
                    if (params.RUN_TESTS) {
                        echo "Running tests..."
                        sh "echo 'Running test commands here'"
                    } else {
                        echo "Skipping tests..."
                    }
                }
            }
        }
    }
}
