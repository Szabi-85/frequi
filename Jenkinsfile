pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Szabi-85/frequi.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    
                    def customImage = docker.build("frequi:${env.BUILD_NUMBER}")
                    
                    docker.withRegistry('http://localhost:5000') {
                        customImage.push()
                        customImage.push("latest")
                    }
                }
            }
        }
    }
}
