pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/kavyapanja/cicd-pipeline-train-schedule-autodeploy.git'  
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ambatilokesh/myimage .'  
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                sh 'docker login -u ambatilokesh -p Lokesh@180900'
                sh 'docker push ambatilokesh/myimage' 
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                // Apply a Kubernetes deployment configuration
                sh '''
                kubectl apply -f /home/ubuntu/deployment.yaml --validate=false
                '''
            }
        } 
    }
}
