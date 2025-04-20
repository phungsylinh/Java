pipeline {
    agent any
    stages {
        stage('Advanced Parallel Example') {
            steps {
                script {
                    def parallelStages = [
                        "Build": {
                            node {
                                try {
                                    echo "Building the application"
                                    // Simulate a build process
                                    sh 'sleep 10'
                                    echo "Build successful"
                                } catch (Exception e) {
                                    echo "Build failed: ${e.getMessage()}"
                                    currentBuild.result = 'FAILURE'
                                    throw e // Re-throw the exception to fail the stage
                                }
                            }
                        },
                        "Test": {
                            node {
                                try {
                                    echo "Running tests"
                                    // Simulate running tests
                                    sh 'sleep 5'
                                    echo "Tests passed"
                                } catch (Exception e) {
                                    echo "Tests failed: ${e.getMessage()}"
                                    currentBuild.result = 'FAILURE'
                                    throw e // Re-throw the exception to fail the stage
                                }
                            }
                        },
                        "Deploy": {
                            node {
                                // Conditional execution: only run if the branch is master
                                when {
                                    branch 'master'
                                }
                                steps {
                                    echo "Deploying to production"
                                    // Simulate deployment
                                    sh 'sleep 2'
                                    echo "Deployment completed"
                                }
                            }
                        }
                    ]
                    parallel parallelStages
                }
            }
        }
    }
}