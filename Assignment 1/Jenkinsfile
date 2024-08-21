pipeline {
    agent any
 
    environment {
        GIT_REPO = 'https://github.com/Priyam-Chowdhury/Jenkins_test.git'
        GIT_BRANCH = 'main'
        PYTHON_FILE = 'test.py'
        DOCKER_IMAGE = 'python:3.9.19-slim-bullseye'
    }
 
    stages {
        stage('Clone Repository') {
            steps {
                sh 'git clone ${GIT_REPO}'
            }
        }
        stage('Run Python Script in Docker') {
            steps {
                script {
                    // Pull the Docker image
                    sh "docker pull ${DOCKER_IMAGE}"
 
                    // Run the Docker container and execute the Python script
                    sh "docker run -v \$(pwd)/Jenkins_test:/usr/src/app -w /usr/src/app ${DOCKER_IMAGE} python ${PYTHON_FILE}"
            }
        }
    }
}
        post {
        always {
            // Clean up workspace
            cleanWs()
        }
    }
}
