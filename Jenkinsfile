pipeline {
    agent {
        kubernetes {
            yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: kubectl
    image: bitnami/kubectl:latest
    command:
    - cat
    tty: true
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
                echo "🔨 Building the application..."
                sh 'echo "Simulating build step"'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running tests..."
                sh 'echo "Simulating test step"'
            }
        }

        stage('Deploy') {
            steps {
                container('kubectl') {
                    echo "🚀 Deploying application..."
                    sh 'kubectl apply -f k8s/deployment.yaml'
                }
            }
        }
    }
}
