pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/kavyapanja/cicd-pipeline-train-schedule-autodeploy.git'  // Replace with your GitHub repository
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ambatilokesh/mynewimage .'  // Build the Docker image
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                sh 'docker login -u ambatilokesh -p Lokesh@180900'
                sh 'docker push ambatilokesh/mynewimage'  // Push the Docker image to Docker Hub
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                // Apply a Kubernetes deployment configuration
                sh '''
                kubectl apply -f kubernetes/deployment.yaml  // Path to your Kubernetes deployment configuration
                '''
            }
        } 
    }
}
