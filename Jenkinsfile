pipeline {
    agent any
    environment {
        my_kubeconfig = credentials('do_kc')
    }
    stages {
        stage('Get Pods') {
            steps {
                sh "kubectl --kubeconfig=$my_kubeconfig  get pods"
                sh "kubectl --kubeconfig=$my_kubeconfig delete -f deployment.yml"
                sh "sleep 10"
                sh "kubectl --kubeconfig=$my_kubeconfig  get pods,svc"
            }
        }
    }
}
