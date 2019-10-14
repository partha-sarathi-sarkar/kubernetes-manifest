pipeline {
  agent { label 'docker' }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  /*triggers {
    cron('@daily')
  }*/
  stages {
    stage('Docker Build') {
      steps {
        sh 'docker build -f "Docker-Manifest/Cointainer1/Dockerfile" -t spartha1995/container-services:containerservice1 .'
        sh 'docker build -f "Docker-Manifest/Cointainer2/Dockerfile" -t spartha1995/container-services:containerservice2 .'
        sh 'docker build -f "Docker-Manifest/helloworld/Dockerfile" -t spartha1995/helloworld .'
      }
    }
    stage('Docker publish') {
      when {
        branch 'master'
      }
      steps {
          sh 'docker push spartha1995/container-services:containerservice1'
          sh 'docker push spartha1995/container-services:containerservice2'
          sh 'docker push spartha1995/helloworld'
      }
    }
  }
}