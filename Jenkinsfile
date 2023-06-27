pipeline{
    agent any
    tools {
        maven 'm1'
    }
    stages {

  stage('clean') {
    steps {
      sh 'mvn clean install'
    }
  }

  stage('test') {
    steps {
      sh 'mvn test'
    }

    post {
      always {
        archiveArtifacts artifacts: 'target/**.jar', followSymlinks: false
        junit 'target/surefire-reports/*.*xml'
      }
    }
  }

  stage('run') {
    steps {
      sh 'chmod 777 scripts/deliver.sh'
      sh './scripts/deliver.sh'
    }
  }

}

}
