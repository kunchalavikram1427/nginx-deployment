pipeline {
    agent any
    environment {
        my_kubeconfig = credentials('do_kc')
    }
    stages {
        stage('Get Pods') {
            steps {
                sh "kubectl --kubeconfig=$my_kubeconfig  get pods"
                sh "kubectl --kubeconfig=$my_kubeconfig apply -f deployment.yml"
                sh "sleep 30"
                sh "kubectl --kubeconfig=$my_kubeconfig  get pods"
            }
        }
    }
}
