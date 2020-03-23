pipeline {
  agent any
  environment {
    shortcommit= sh (script: 'git rev-parse --short HEAD', returnStdout: true)
  } 
  stages{
    stage('Build') {
      steps {
          sh 'mvn package'
      }
    }
    stage('Package') {
     steps {
        script {
          def commitid = echo "${env.shortcommit}"
          sh 'docker build -t shunya:${commitid} .'
        }
      }
    }
  }
}
