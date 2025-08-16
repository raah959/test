pipeline {
  agent {
    label 'jenkins-agent'  // use the label you assigned
  }

  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/raah959/test.git'
      }
    }

    stage('Build') {
      steps {
        echo "🔨 Building..."
      }
    }

    stage('Deploy') {
      steps {
        sh 'kubectl apply -f k8s/deployment.yaml'
      }
    }
  }
}
