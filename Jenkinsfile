pipeline {
  agent any
  //JAVA와 Maven Tool 등록
  tools {
    jdk 'jdk17'
    maven 'M3'
  }

  stages {
    // GitHub에서 Jenkins소스코드 복사
    stage('Git Clone'){
      step{
        git url: 'https://github.com/jsshubs/spring-petclinic.git', branch: 'main'
        
      }

    }
    stage('Maven Build'){
      step{

      }
    }
    stage('Docker Image'){

    }
    stage('Docker Image Push'){

    }
    stage('SSH Publish'){
      
    }

  }

}
