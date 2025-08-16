pipeline {
  agent {
    label 'jenkins-agent' 
  }

  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/raah959/test.git'
      }
    }

    stage('Deploy') {
      steps {
        sh 'kubectl apply -f k8s/deployment.yaml'
      }
    }
  }
}
