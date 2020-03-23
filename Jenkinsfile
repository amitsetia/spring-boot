pipeline {
  agent any
  environment {
    shortcommit= sh (script: 'git rev-parse --short HEAD', returnStdout: true)
  } 
  stages{
    stage('build') {
      steps {
          sh 'mvn package'
      }
    }
    stage('Package') {
     steps {
          sh (script: 'docker build -t shunya/spring-dec:${env.shortcommit} .')
      }
    }
  }
}
