pipeline {
    agent any
    stages {
        stage('Parallel Example') {
            steps {
                script {
                    def parallelStages = [
                        "Stage 1": {
                            node {
                                echo "Running Stage 1 on ${NODE_NAME}"
                                sleep 5
                                echo "Stage 1 completed"
                            }
                        },
                        "Stage 2": {
                            node {
                                echo "Running Stage 2 on ${NODE_NAME}"
                                sleep 3
                                echo "Stage 2 completed"
                            }
                        }
                    ]
                    parallel parallelStages
                }
            }
        }
    }
}