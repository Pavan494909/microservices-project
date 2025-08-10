pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myeks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapp', serverUrl: 'https://D11C312C2219E88506586C802B2823FF.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myeks-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapp', serverUrl: 'https://D11C312C2219E88506586C802B2823FF.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapp"
                }
            }
        }
    }
}
