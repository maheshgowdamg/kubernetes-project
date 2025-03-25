pipeline {
    agent any
    stages {
        stage('Pull Source') {
            steps {
                git branch: 'main', url: 'https://github.com/maheshgowdamg/kubernetes-project.git'
            }
        }
        stage('Build and Deploy') {
            steps {
                script {
                    // Kubernetes plugin configuration
                    kubernetesDeploy(configs: 'deploy.yml', kubeconfigId: 'kube-config')
                }
            }
        }
    }
}
