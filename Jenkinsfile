pipeline {
    agent any
    stages{
        stage('Checking Out Repo'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/AfA-Navtaaz/YogaForm-React-Firebase-.git']]])
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t navtaaz/devopsone .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhubpwd')]) {
                   sh 'docker login -u navtaaz -p ${dockerhubpwd}'

}
                   sh 'docker push navtaaz/devopsone'
                }
            }
        }
    }
}
