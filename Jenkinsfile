pipeline {
    agent {
        docker {
            image 'bitnami/kubectl:latest'
            args '-v /root/.kube:/root/.kube'
        }
    }
    stages {
        stage('Deploy') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
            }
        }
    }
}
