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
                    docker.withRegistry("https://registry.hub.docker.com", "docker") {
                        dockerapp.push("${env.BUILD_NUMBER}");
                        dockerapp.push("latest");
                    }
                }
            }
        }

        stage ("Deploy") {
            steps {
                script {
                    withKubeConfig([credentialsId: "kubeconfig"]) {
                        sh "kubectl apply -f ./src/kubernetes/"
                    }
                }
            }
        }
    }
}