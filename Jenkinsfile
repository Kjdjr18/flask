pipeline {
    environment {
        registry = 'kjdjr18/flask_app'
        registryCredentials = 'docker'
        cluster_name = 'skillstorm'
    }
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/Kjdjr18/flask', branch: 'main')
      }
    }
stage('Build Stage') {
    steps {
        script {
            dockerImage = docker.build(registry)
        }
    }
}
stage('Deploy Stage') {
    steps {
        script {
            docker.withRegistry('', registryCredentials) {
                dockerImage.push()
            }
        }
    }
}
  }
}
