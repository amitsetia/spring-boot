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
     agent any
     steps {
          sh 'docker build -t shunya/spring-petclinic:${env.shortcommit} .'
            //echo 'Starting to build docker image'
            //script {
            //def dockerfile = 'Dockerfile'
            //def image = docker.build("springdec:${env.shortcommit} ")
            //} 
           }  
    }
}
}
