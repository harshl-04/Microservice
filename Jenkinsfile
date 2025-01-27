pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'HARSH-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E20128D13F56F742CC2067C4E14BEFE0.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'HARSH-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E20128D13F56F742CC2067C4E14BEFE0.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
