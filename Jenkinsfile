pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git Clone') {
      steps {
        git(url: 'https://github.com/rajanpbg/mithun_spring-boot-mongo-docker.git', branch: 'master', credentialsId: 'GIT_credentials')
      }
    }

    stage('maven build') {
      steps {
        sh 'mvn clean install -Dlicense.skip=true'
      }
    }

    stage('Docker Build') {
      steps {
        sh 'docker build -t rajanpbg/spring-boot-mongo .'
      }
    }

  }
}