pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'diwakar1823/jenkins-demo'  // Docker image name
        GITHUB_REPO = 'https://github.com/diwakar1823/jenkins-pipeline'  // Your GitHub repo URL
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the code from the GitHub repository
                git url: "$GITHUB_REPO", branch: 'master'  // Ensure correct branch name
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t $DOCKER_IMAGE .'
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    // Login to Docker Hub with hardcoded credentials (for testing only)
                    sh 'docker login -u diwakar1823 -p Asdfghjkl@123'  // Replace with your Docker Hub username and password
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    // Push the Docker image to Docker Hub
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }

    post {
        success {
            echo "Build and push to Docker Hub successful!"
        }

        failure {
            echo "Something went wrong with the pipeline."
        }
    }
}
