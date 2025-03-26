pipeline {
    agent any

    environment {
        KUBECONFIG = credentials('kube')  // Use Jenkins credential ID
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/maheshgowdamg/kubernetes-project.git'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    kubernetesCli(
                        kubeconfigId: 'kubeconfig-jenkins',
                        script: '''
                        kubectl apply -f deploy.yml
                        kubectl get pods
                        '''
                    )
                }
            }
        }
    }
}
