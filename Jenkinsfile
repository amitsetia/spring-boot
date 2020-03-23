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
           echo 'Starting to build docker image'
           script {
            def dockerfile = 'Dockerfile.test'
            def image = docker.build("springdec:${env.shortcommit}", "-f ${dockerfile} ./")
           } 
           }  
    }
}
}
