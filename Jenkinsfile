pipeline {
    agent any

    stages {
        stage('Deploy To kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k-token', namespace: 'webapps', serverUrl: 'https://8EC5F8F1AFE029D1A336E94B7A015DF5.gr7.us-west-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        
         stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k-token', namespace: 'webapps', serverUrl: 'https://8EC5F8F1AFE029D1A336E94B7A015DF5.gr7.us-west-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
