pipeline {
    agent any 

    stages {

        stage ("Build Image Docker") {
            steps {
                script {
                    dockerapp = docker.build "charleszt/kube-news:${env.BUILD_NUMBER}", "./src/."
                }
            }
        }

        stage ("Send Image for Docker Hub") {
            steps {
                script {
                    docker.withRegistry("https://registry.hub.docker.com/v2/", "docker") {
                        dockerapp.push(${env.BUILD_NUMBER});
                    }
                }
            }
        }
    }
}