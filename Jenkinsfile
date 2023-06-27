pipeline{
    agent any
    tools {
        maven 'm1'
    }
    stages {

  stage('clean') {
    steps {
      sh 'mvn clean'
    }
  }
stage('build') {
    steps {
      sh 'mvn install'
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

  
}

}
