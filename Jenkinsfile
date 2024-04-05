pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Updating Packages"'
                sh 'sudo apt update'
                sh 'echo "build Dockerfile into image"'
                sh 'docker build -t my-node-app .'

                // Your build steps here
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Verifying that the docker image has been built"'
                sh 'docker images'
                // Your test steps here
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Run the Docker image as a container"'
                sh 'docker run -p 3000:3000 my-node-app'
                sh 'npm start'

                // Your deployment steps here
            }
        }
    }
    post {
        always {
            // Clean up Docker containers after the pipeline execution
            cleanWs()
        }
    }
}
