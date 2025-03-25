pipeline{
    agent any
    stages{
         stage('pull src'){
            steps{
                git branch: 'main', url: 'https://github.com/maheshgowdamg/kubernetes-project.git' 
            }
        }
        stage('build'){
            steps{
                 sh 'kubectl apply -f deploy.yml'
            }
        }


    } 
}
