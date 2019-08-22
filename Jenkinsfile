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
                    docker.withRegistry('929444784092.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:7d072b26-ca5f-4a96-93bc-885bab7f5b00') {
                        docker.image('dimi-nginx').push('latest')
                    }
                }
            }
        }
    }
}
