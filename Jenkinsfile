pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'web'
        CONTAINER_NAME = 'angry_moser'
        PORT_MAPPING = '8089:80'  // Adjust the port mapping as needed
    }

    stages {
        // stage('Checkout') {
        //     steps {
        //         // Clean workspace before checkout
        //         deleteDir()
        //         // Checkout the HTML source code from GitHub
        //         git url: 'https://github.com/andrinahaura/project1.git'
        //     }
        // }
        //     stage('Checkout') {
        //         steps {
        //             deleteDir()
        //             checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/tasyasyf/cv.git']]])
        //         }
        //     }

        // stage('Build Docker Image') {
        //     steps {
        //         script {
        //             dir('project1') {x
        //                 // Build Docker image dengan konten HTML
        //                 docker.build("${DOCKER_IMAGE}", '-f  Dockerfile .')
        //             }
        //             // // Build Docker image with the HTML content
        //             // docker.build("${DOCKER_IMAGE}", '-f Dockerfile .')
        //         }
        //     }
        // }

    
        stage('Run sssDocker Container') {
            steps {
                script {
                    // Run Docker container based on the built image
                    docker.image("${DOCKER_IMAGE}").run("-p ${PORT_MAPPING} --name ${CONTAINER_NAME}")
                }
            }
        }
    }

    post {
        always {
            script {
                // Stop and remove the Docker container after execution
                docker.image("${DOCKER_IMAGE}").stop()
                docker.image("${DOCKER_IMAGE}").remove()
            }
        }
    }
}