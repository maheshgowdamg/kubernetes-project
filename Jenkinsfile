pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('pull src'){
            steps{
                
            }
        }
        stage('build'){
            sh 'mvn clean package'
        }
        stage('remove conatiner'){
            steps{
                sh 'docker rm -f $(docker ps -aq) || true'
                sh 'docker container prune -f'
            }
        }
        stage('remove images'){
            steps{
                sh 'docker rmi -f $(docker images -q) || true'
            }
        }
        stage('build image'){
            steps{
                sh 'docker build -t kube .'
            }
        }
        stage('tag image'){
            steps{
                sh 'docker tag kube maheshgowdamg25/kube:latest'
            }
        }
        stage('push image'){
            steps{
                sh 'echo "Mahi@2001"|docker login -u maheshgowdamg25 --password-stdin'
                sh 'docker push maheshgowdamg25/kube:latest'
            }
        }
        stage('run container'){
            steps{
                sh 'docker run -d -p 8081:8081 maheshgowdamg25/kube:latest'
            }
        }
    }
}