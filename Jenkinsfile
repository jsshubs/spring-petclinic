pipeline {
  agent any
  //JAVA와 Maven Tool 등록
  tools {
    jdk 'JDK17'
    maven 'M3'
  }

  //Docker Hub 접속 정보
  environment{
    DOCKERHUB_CREDENTIALS = credentials('dockerCredentials')
    AWS_CREDENTIALS = credentials('AWSCredentials')
    GIT_CREDENTIALS = credentials('gitCredentials')
    REGION = 'ap-northeast-2'
  }

  
  stages {
    stage('Git Clone') {
      steps {
        echo 'Git Clone'
        gir url: 'https://https://github.com/jsshubs/spring-petclinic'
         branch: 'main', credentialIdL: 'GIT_CREDENTIALS'
      }
   
  }      
 }
}
