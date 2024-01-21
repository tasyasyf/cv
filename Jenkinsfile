pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the HTML source code from GitHub
                git 'https://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@github.com/andrinahaura/project1.git'
            }
        }

        stage('Build HTML') {
            steps {
                // Your build steps for HTML, e.g., using a static site generator
                // Example: Assuming you have an index.html in the root
                sh 'ls -l'  // Add your build commands here
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image with the HTML content
                    docker.build('ola', '.')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run Docker container based on the built image
                    docker.run('-p 8089:89 --name ola')
                }
            }
        }
    }

    post {
        always {
            script {
                // Stop and remove the Docker container after execution
                docker.image('ola').stop()
                docker.image('ola').remove()
            }
        }
    }
}