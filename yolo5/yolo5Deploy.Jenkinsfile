pipeline {
    agent any
    
    stages {
        stage('Deploying') {
            steps {
                sh '''
                aws eks --region us-east-2 update-kubeconfig --name k8s-batch1
                kubectl config set-context --current --namespace=shweta-ns
                '''
            }
        }
    }
   
    
   
    parameters { 
        string(name: '854171615125.dkr.ecr.us-east-2.amazonaws.com/shweta-jenkins-yolo5:0.0.1', defaultValue: '', description: '')
     }

   
}
