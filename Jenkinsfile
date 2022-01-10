pipeline {
    agent {
    docker {
        image 'ubuntu:latest'
        //label 'latest'
        //repository/docker/gaddamnarendra/myprivaterepo
        registryUrl 'https://hub.docker.com/'
        registryCredentialsId 'DOCKER_CRDS'
    }
}
  /*environment {
    DOCKERHUB_CREDENTIALS = credentials('DOCKER_CRDS')
  }*/
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t gaddamnarendra/maven:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push gaddamnarendra/maven:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
