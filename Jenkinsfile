pipeline {
    agent any

    environment {
        KUBECONFIG_CREDENTIALS = credentials('kubeconfig')
    }

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // ใช้ kubeconfig ในการ deploy
                    withCredentials([file(credentialsId: 'kubeconfig', variable: 'KUBECONFIG')]) {
                        sh 'kubectl apply -f app/deployment.yaml --kubeconfig=$KUBECONFIG'
                    }
                }
            }
        }
    }
}
