pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/SarhanMoh/final-python', changelog: true, poll: true, branch: 'main')
      }
    }

    stage('build') {
      steps {
        sh 'docker build -t test:$BUILD_ID .'
      }
    }

    stage('run & test') {
      steps {
        sh 'docker run --name test -d -p 9229:9230 test:$BUILD_ID'
        sleep 3
        sh 'curl localhost:8080'
        sh 'docker stop test && docker rm test'
      }
    }

  }
}