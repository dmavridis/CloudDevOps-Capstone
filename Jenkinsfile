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
                    docker.build('dimi-app')
                }
//                docker.withRegistry('929444784092.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:dimi-nginx') {
//                    docker.image('dimi-app').push('latest')
//                }
                
            }
        }
    }
}
