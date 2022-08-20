pipeline {
    agent any
    stages {
        stage('Get Pods') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'do_kc']) {
                        sh 'helm repo add bitnami https://charts.bitnami.com/bitnami'
                        sh 'helm repo update'
                        sh 'helm upgrade --install demo bitnami/nginx --set service.type=NodePort'
                        sh "kubectl get pods,svc"
                        sh "sleep 10"
                        sh "kubectl get pods,svc"
                    }
                }               
            }
        }
    }
}
