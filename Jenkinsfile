pipeline {
    agent any

    environment {
        BACKEND_IMAGE = "mern-backend"
        FRONTEND_IMAGE = "mern-frontend"
        DOCKER_HUB_CREDENTIALS = credentials('docker-hub-credentials')
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-repo/your-project.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                script {
                    dir('backend') {
                        sh 'docker build -t $BACKEND_IMAGE .'
                    }
                }
            }
        }

        stage('Build Frontend Image') {
            steps {
                script {
                    dir('frontend') {
                        sh 'docker build -t $FRONTEND_IMAGE .'
                    }
                }
            }
        }

        stage('Push Images to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'DOCKER_HUB_CREDENTIALS') {
                        sh 'docker tag $BACKEND_IMAGE $DOCKER_HUB_CREDENTIALS_USR/$BACKEND_IMAGE'
                        sh 'docker tag $FRONTEND_IMAGE $DOCKER_HUB_CREDENTIALS_USR/$FRONTEND_IMAGE'
                        sh 'docker push $DOCKER_HUB_CREDENTIALS_USR/$BACKEND_IMAGE'
                        sh 'docker push $DOCKER_HUB_CREDENTIALS_USR/$FRONTEND_IMAGE'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Pull and run the images on the target server
                    // Adjust the commands as necessary for your deployment environment
                    sh '''
                        docker pull $DOCKER_HUB_CREDENTIALS_USR/$BACKEND_IMAGE
                        docker pull $DOCKER_HUB_CREDENTIALS_USR/$FRONTEND_IMAGE
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
