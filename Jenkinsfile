pipeline{
    agent any

    environment{
        KUBECONFIG = '/home/sumit/.kube/config'
    }

    stages{
        stage('git clone'){
            steps{
                git branch: 'main', credentialsId: 'ed22fdee-75de-49be-b696-549a31ed6c68', url: 'https://github.com/iamsumitkumar10/creative-project-k8'
            }
        }

        stage('check all pods'){
            steps{
                sh 'kubectl get pods'
            }
        }
        stage('deploy deployment'){
            steps{
                sh 'kubectl apply -f backend-deployment.yaml'
                sh 'kubectl apply -f frontend-deplyment.yaml'
            }
        }
        stage('services'){
            steps{
                sh 'kubectl apply -f backend-service.yaml'
                sh 'kubectl apply -f frontend-service.yaml'
            }
        }
    }
}