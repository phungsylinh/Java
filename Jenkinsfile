pipeline {
    agent any
    stages {
        stage('Combined Example') {
            matrix {
                axes {
                    axis {
                        name 'BROWSER'
                        values 'Chrome', 'Firefox'
                    }
                }
                stages {
                    stage('Parallel Tests') {
                        steps {
                            script {
                                def parallelTests = [
                                    "Unit Tests": {
                                        node {
                                            echo "Running Unit Tests on ${BROWSER}"
                                            sh "echo Running Unit Tests on ${BROWSER}"
                                        }
                                    },
                                    "Integration Tests": {
                                        node {
                                            echo "Running Integration Tests on ${BROWSER}"
                                            sh "echo Running Integration Tests on ${BROWSER}"
                                        }
                                    }
                                ]
                                parallel parallelTests
                            }
                        }
                    }
                }
            }
        }
    }
}