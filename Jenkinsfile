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
          def commitid = ${env.shortcommit}
          sh 'docker build -t shunya:${commitid} .'
        }
      }
    }
  }
}
