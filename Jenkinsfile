pipeline {
    agent any
    stages {
        // stage('Get Pods') {
        //     steps {
        //         sh "kubectl --kubeconfig=$my_kubeconfig  get pods"
        //         sh "kubectl --kubeconfig=$my_kubeconfig apply -f deployment.yml"
        //         sh "sleep 30"
        //         sh "kubectl --kubeconfig=$my_kubeconfig  get pods"
        //     }
        // }
        stage('Get Pods') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'do_kc']) {
                        sh 'helm repo add bitnami https://charts.bitnami.com/bitnami'
                        sh 'helm repo update'
                        sh 'helm upgrade --install demo bitnami/nginx --set service.type=LoadBalancer'
                        sh 'helm uninstall demo'
                        sh "kubectl get pods,svc"
                        sh "sleep 10"
                        sh "kubectl get pods,svc"
                    }
                }               
            }
        }
    }
}
