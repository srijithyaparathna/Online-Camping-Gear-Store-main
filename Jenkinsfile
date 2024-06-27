pipeline {
    agent any

    environment {
        BACKEND_IMAGE = "backend"
        FRONTEND_IMAGE = "frontend"
    }

    stages {
        stage('Clone Repository') {
            steps {
                checkout scm    
            }
        }

        // Add your other stages here for building images and deploying
    }

    post {
        always {
            cleanWs()
        }
    }
}
