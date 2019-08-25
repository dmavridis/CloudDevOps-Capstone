pipeline {
    agent any
    stages {
        stage('Lint HTML'){
            steps{
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload Docker to ECR') {
            steps {
                sh 'echo "Building docker image "'
                script{
                    docker.build('dimi-nginx')
                    docker.withRegistry('https://929444784092.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:7d072b26-ca5f-4a96-93bc-885bab7f5b00') {
                        docker.image('dimi-nginx').push('latest')
                    }
                }
            }
        }
        stage('Remove current cluster from EKS'){
            steps{
                withKubeConfig([credentialsId: '929444784092', serverUrl:' https://9705639DB1B9054B46FD3B8A1FCA64EB.yl4.us-east-1.eks.amazonaws.com']){
                    sh 'kubectl delete deployment.apps/dimicloud'
                }
            }
        }
//        stage('Deploy image to EKS'){
//            steps{
//                sh 'kubectl apply -f deployment.yaml'
//            }
//        }       
    }
}
