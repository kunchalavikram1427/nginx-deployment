pipeline {
    agent any
    environment {
        my_kubeconfig = credentials('do_kc')
    }
    stages {
        stage('Get Pods') {
            steps {
                sh 'mkdir -p  ./kube/config'
                sh "cat $my_kubeconfig > ./kube/config"
                sh "kubectl get pods"
                sh "kubectl apply -f deployment.yml"
                sh "sleep 10"
                sh "kubectl get pods,svc"
            }
        }
    }
}
