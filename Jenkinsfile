pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/raah959/test.git',
                    credentialsId: 'github-creds'
            }
        }

        stage('Deploy to Minikube') {
            steps {
                sh '''
                echo "Applying Kubernetes manifests..."
                kubectl apply -f k8s/deployment.yaml
                kubectl apply -f k8s/service.yaml
                kubectl get pods -n default
                '''
            }
        }
    }
}
