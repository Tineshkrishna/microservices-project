pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'tpEKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://799EF0560C960765C23BED20570953CC.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'tpEKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://799EF0560C960765C23BED20570953CC.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
