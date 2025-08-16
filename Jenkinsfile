pipeline {
  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: jnlp
    image: jenkins/inbound-agent:latest
    args: ['\$(JENKINS_SECRET)', '\$(JENKINS_NAME)']
  - name: kubectl
    image: bitnami/kubectl:latest
    command:
    - sleep
    args:
    - 99d
"""
    }
  }

  stages {
    stage('Clone') {
      steps {
        git branch: 'main',
            url: 'https://github.com/raah959/test.git'
      }
    }

    stage('Build') {
      steps {
        echo "🔨 Building..."
      }
    }

    stage('Deploy') {
      steps {
        container('kubectl') {
          sh 'kubectl apply -f k8s/deployment.yaml'
        }
      }
    }
  }
}
