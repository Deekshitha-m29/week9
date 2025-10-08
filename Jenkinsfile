pipeline{
    agent any
    stages{
        stage('Build docker image'){
            steps{
                echo 'Building Docker image...'
                bat 'docker build -t kubdemoapp:v1 .'
            }
        }
        stage('Docker login'){
            steps{
                bat 'docker login -u "Deekshu209" -p "Admins209"'
            }
        }
        stage('Push docker Image to Docker hub'){
            steps{
                echo 'Pushing Docker image to Docker Hub...'
                bat 'docker tag kubdemoapp:v1 Deekshu209/sample:kubeimage1'
                bat 'docker push Deekshu209/sample:kubeimage1'
            }
        }
        stage('Deploy to Kubernetes'){
            steps{
                bat  'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f serive.yaml'
            }
        }
    }
    post{
        success{
            echo 'Pipeline completed successfully!'
        }
        failure{
            echo 'Pipeline failed. Please check the logs.'
        }
    }

}
