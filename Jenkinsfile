pipeline {
    agent any

    triggers {
        // GitHub PR trigger (This listens for PR events)
        githubPush()
    }

    environment {
        GIT_BRANCH = 'main'  // Branch to track, e.g., 'main'
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the PR branch
                checkout scm
            }
        }

        // stage('Validate PR') {
        //     steps {
        //         script {
        //             // Ensure we are dealing with a PR to main
        //             def prTargetBranch = env.CHANGE_TARGET
        //             if (prTargetBranch != GIT_BRANCH) {
        //                 error "This PR is not targeting the 'main' branch!"
        //             } else {
        //                 echo "This PR is targeting the 'main' branch"
        //             }
        //         }
        //     }
        // }

        stage('Build & Test') {
            steps {
                script {
                    // Your build and test steps go here
                    echo "Building and testing the code..."
                    // e.g., sh 'make build && make test'
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                script {
                    // Deploy the changes (optional stage)
                    echo "Deploying the code..."
                    // e.g., sh './deploy.sh'
                }
            }
        }
    }

    post {
        always {
            echo "This runs after the pipeline execution"
        }
        success {
            echo "This runs if the pipeline is successful"
        }
        failure {
            echo "This runs if the pipeline fails"
        }
    }
}
