pipeline {
    environment{
        registry= "fouadsaididev/tp5"
        registryCredential='ec82ab60-607c-4705-90b7-056df5b67d78'
        dockerImage=''
    }
    agent any
    stages{
        stage('Cloning Git'){
            steps{
                git 'https://github.com/fouad-saidi-dev/devops-jenkins'
            }
        }
        stage('Building image'){
            steps{
                script{
                    dockerImage=docker.build registry+":$BUILD_NUMBER"
                }
            }
        }
        stage('Test image'){
            steps{
                script{
                    echo "Tests passed"
                }
            }
        }
        stage('Publish Image'){
            steps{
                script{
                    docker.withRegistry('',registryCredential){
                        dockerImage.push()
                    }
                }
            }
        }
    }
}