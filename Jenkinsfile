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
    }
}