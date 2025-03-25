pipeline {
    agent { label 'k8s-pod' } 

    environment {
        KUBECONFIG = credentials('kubeconfig')  
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                   
                    git branch: 'main', url: 'https://github.com/maheshgowdamg/kubernetes-project.git'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    
                    sh 'kubectl apply -f deploy.yml'
                }
            }
        }
    }
}
