pipeline {
     agent any

    parameters { 
        string(name: '854171615125.dkr.ecr.us-east-2.amazonaws.com/shweta-jenkins:0.0.9', defaultValue: '', description: '')
         }
    
    environment {
        AWS_REGION_K8S = 'us-east-2'
        K8S_CLUSTER_NAME = 'k8s-batch1'
        K8S_NAMESPACE = 'shweta-ns'
        MANIFEST_FILE = 'yolo5-deployment.yaml'
    }
    stages {
        stage('Start Deploying') {
            steps {
                    sh 'echo "Deploying process started"'
            }
        }
        stage('Connect to the k8s cluster') {
            steps {
                    sh 'aws eks --region ${AWS_REGION_K8S} update-kubeconfig --name ${K8S_CLUSTER_NAME}'
            }
        }
        stage('Setting default namespace') {
            steps {
                    sh 'kubectl config set-context --current --namespace=${K8S_NAMESPACE}'
            }
        }
        stage('Deploying on k8s') {
            steps {
                   sh '''
                        cd "yolo5"
                        kubectl apply -f ${MANIFEST_FILE}
                   '''
            }
        }
        stage('Finish Deploying') {
            steps {
                   sh 'echo "Deploying Process Finished" '
            }
        }
    }


}