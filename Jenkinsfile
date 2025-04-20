pipeline {
    agent any

    stages {
        stage('Matrix with Parallel') {
            matrix {
                axes {
                    axis {
                        name 'OS'
                        values 'linux', 'windows'
                    }
                    axis {
                        name 'JDK'
                        values '11', '17'
                    }
                }

                stages {
                    stage('Parallel Tasks') {
                        parallel {
                            stage('Unit Test') {
                                steps {
                                    echo "Running Unit Test on ${OS} with JDK ${JDK}"
                                    sh "echo unit test"
                                }
                            }

                            stage('Integration Test') {
                                steps {
                                    echo "Running Integration Test on ${OS} with JDK ${JDK}"
                                    sh "echo integration test"
                                }
                            }

                            stage('Lint') {
                                steps {
                                    echo "Running Lint on ${OS} with JDK ${JDK}"
                                    sh "echo lint"
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
