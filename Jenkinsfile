pipeline {
  agent any
 
  stages{
    stage('build') {
      steps {
           sh 'mvn package'
        }
    }
    stage('Package') {
     steps {
           sh "docker build -t springtest:${BUILD_TIMESTAMP} ."
           }  
    }
}
}
