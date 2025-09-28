pipeline {
    agent {
        
        label 'docker'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    
                    sh 'docker build -t thomaseidg/d-pro -f Dockerfile.dev .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    env.DOCKER_BUILDKIT = 1
                    sh 'docker run -e CI=true homaseidg/d-pro npm run test'
                }
            }
        }
    }
}