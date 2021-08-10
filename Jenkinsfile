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
      agent {
        node {
          label 'docker'
        }

      }
      steps {
        sh 'mvn clean install '
      }
    }

    stage('Docker Build') {
      agent {
        node {
          label 'docker'
        }

      }
      steps {
        sh 'docker build -t dockerhandson/spring-boot-mongo .'
      }
    }

    stage('error') {
      agent {
        node {
          label 'docker'
        }

      }
      steps {
        kubernetesDeploy(configs: 'springBootMongo.yml', kubeconfigId: 'KUBECONFIG_LOCAL')
      }
    }

  }
  tools {
    maven 'maven'
  }
}