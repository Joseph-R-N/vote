pipeline {
    agent any
    stages{
        stage ('Git Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Joseph-R-N/vote.git']]])
            }
        }
        stage ('Docker Build') {
            steps {
                sh 'docker build -t nelrajan/vote . '
            }
        }
            
        stage ('Docker Push image') {
            steps {
                withDockerRegistry(credentialsId: 'dockerhub', url:'') {
                    sh 'docker push nelrajan/vote'
                }
            }
        }
        
    }
}
