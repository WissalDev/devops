pipeline {
    environment {
    registry = "wissaltazi/tp2"
    registryCredential = 'bac14f21-a0dd-49ed-a8b8-e9c74dbd5d9d'
    dockerImage = ''
    }
    agent any
    stages {
        stage('Cloning Git') {
            steps {
                git branch: "main", url: 'https://github.com/WissalDev/devops'
            }
        }
        stage('Building image') {
            steps{
                script{
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Test image') {
            steps{
                script{
                    echo "Tests passed"
                }
            }
        }
        stage('Publish Image') {
            steps{
                script {
                    docker.withRegistry( '', registryCredential ) {
                    dockerImage.push()
                    }
                }
            }
        }
    }
}