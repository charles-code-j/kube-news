pipeline {
    agent any 

    stages {

        stage ("Build Image Docker") {

            steps {
                dockerapp = docker.build "charleszt/kube-news:${env.BUILD_NUMBER}", "."
            }
        }
    }
}