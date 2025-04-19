pipeline {
  agent any

  stages {
    stage('Clone source') {
      steps {
        git 'https://github.com/phungsylinh/Java.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
          scp target/hello-maven.jar user@server:/opt/app/
          ssh user@server 'pkill -f hello-maven.jar || true && java -jar /opt/app/hello-maven.jar &'
        '''
      }
    }
  }
}
