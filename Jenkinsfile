@Library('shared-utils@main') _
import com.example.MyHelper

pipeline {
    agent any
    stages {
        stage('Generate Random String') {
            steps {
                script {
                    String randomString = MyHelper.generateRandomString(10)
                    echo "Random String: ${randomString}"
                }
            }
        }
    }
}