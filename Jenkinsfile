pipeline {
    agent any
    stages {
        stage('Get Pods') {
            steps {
                script {
                    withKubeConfig([credentialsId: 'do_kc']) {
                        sh "kubectl get pods,svc"
                        sh 'kubectl apply -f deployment.yml'
                        sh "sleep 10"
                        sh "kubectl get pods,svc"
                    }
                }               
            }
        }
    }
}
