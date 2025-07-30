pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myeks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapp', serverUrl: 'https://E7630574AFF1D95D9C7F037EF23A8C86.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myeks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapp', serverUrl: 'https://E7630574AFF1D95D9C7F037EF23A8C86.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapp"
                }
            }
        }
    }
}
