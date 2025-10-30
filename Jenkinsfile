pipeline {
    agent any
   
       stages{
        stage('Docker Login') {
            steps {
                  bat 'docker login -u sparshitha -p 0213@Csptha'
                }
            }
        stage('push Docker Image to Docker Hub') {
            steps {
                echo "push Docker Image to Docker Hub"
                bat "docker tag seleniumdemoapp:v1 sparshitha/sample:seleniumtestimage"               
                    
                bat "docker push sparshitha/sample:seleniumtestimage"
                
            }
        }
        stage('Deploy to Kubernetes') { 
            steps { 
                    
                    bat 'kubectl apply -f deployment.yaml --validate=false' 
                    bat 'kubectl apply -f service.yaml' 
            } 
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}




