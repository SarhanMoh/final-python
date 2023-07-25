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
        sh 'docker run --name test1 -d -p 9229:9230 test:$BUILD_ID'
        sleep 3
        sh 'curl localhost:8080'
        sh 'docker stop test1 && docker rm test1'
      }
    }

    stage('UPLOAD') {
      steps {
        sh 'docker tag test1:$BUILD_ID sarhanmo/final-python:$BUILD_ID'
        sh 'docker login -u sarhanmo -p Mohammad-99'
        sh 'docker push sarhanmo/final-python:$BUILD_ID'
      }
    }

  }
}