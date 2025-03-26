pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/maheshgowdamg/kubernetes-project.git'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig([credentialsId: 'kube']) {
                    sh '''
                        kubectl apply -f deploy.yml
                        kubectl get pods
                    '''
                }
            }
        }
    }
}
