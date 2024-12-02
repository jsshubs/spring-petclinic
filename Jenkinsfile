pipeline {
  agent any
  //JAVA와 Maven Tool 등록
  tools {
    jdk 'jdk17'
    maven 'M3'
  }

  //Docker Hub 접속 정보
  environment{
    DOCKER_CREDENTIALS = credentials('dockerCredentials')
  }

  
  stages {
    // GitHub에서 Jenkins소스코드 복사
    stage('Git Clone'){
      steps{
        git url: 'https://github.com/jsshubs/spring-petclinic.git', branch: 'main'
      }

    }
    stage('Maven Build'){
      steps{
        sh 'mvn -Dmaven.test.failure.ignore=true clean package'
      }
    }
    stage('Docker Image'){
      steps{
        dir("${env.WORKSPACE}") {
          sh """
          docker build -t jeongsik4/spring-petclinic:$BUILD_NUMBER .
          docker tag jeongsik4/spring-petclinic:$BUILD_NUMBER jeongsik4/spring-petclinic:latest
          """
        }
      }
    }
  stage('Docker Image Push'){
    steps{
    sh """
    echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin
    docker push jeongsik4/spring-petclinic:latest
    """
    }
  }

  }

}
