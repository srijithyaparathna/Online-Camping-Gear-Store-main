pipeline {
    agent any

    environment {
        BACKEND_IMAGE = "backend"
        FRONTEND_IMAGE = "frontend"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/srijithyaparathna/Online-Camping-Gear-Store-main'
            }
        }

        stage('Build Backend Image') {
            steps {
                script {
                    dir('backend') {
                        bat 'docker build -t %BACKEND_IMAGE% .'
                    }
                }
            }
        }

        stage('Build Frontend Image') {
            steps {
                script {
                    dir('frontend') {
                        bat 'docker build -t %FRONTEND_IMAGE% .'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Pull and run the images on the target server
                    // Adjust the commands as necessary for your deployment environment
                    bat '''
                        docker pull %DOCKER_HUB_CREDENTIALS_USR%/%BACKEND_IMAGE%
                        docker pull %DOCKER_HUB_CREDENTIALS_USR%/%FRONTEND_IMAGE%
                        docker-compose up -d
                    '''
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
