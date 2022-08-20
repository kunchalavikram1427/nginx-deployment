pipeline {
    agent any
    environment {
        my_kubeconfig = credentials('do_kc')
    }
    stages {
        stage('Get Pods') {
            steps {
                sh "kubectl --kubeconfig=$my_kubeconfig  get pods"
            }
        }
    }
}
