pipeline {
  agent any
  environment {
    shortcommit = sh "git rev-parse --short HEAD"
  } 
  stages{
    stage('build') {
      steps {
           sh 'mvn package'
        }
    }
    stage('Package') {
     steps {
           sh "docker build -t springtest/decpip:${shortcommit} ."
           }  
    }
}
}
