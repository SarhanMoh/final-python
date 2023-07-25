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

  }
}