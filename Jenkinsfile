pipeline {
  agent any
  environment {
    shortcommit= sh (script: 'git rev-parse --short HEAD', returnStdout: true).trim()
  } 
  stages{
    stage('Build') {
      steps {
          sh 'mvn package'
      }
    }
    stage('Package') {
      steps {
          sh "docker build -t setiaamit/shunya:${env.shortcommit} ."
      }
    }
    stage('Publish'){
      steps{
        withDockerRegistry(credentialsId: 'Docker', url: '') {
          sh "docker push setiaamit/shunya:${env.shortcommit}"
        }
      }
    }
  }
}
