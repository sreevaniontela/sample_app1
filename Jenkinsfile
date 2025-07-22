pipeline{
    agent any 
    tools{
        maven 'maven1'
    }
    environment{
        image_name = 'gopi1996/speed'
        image_tag = "${env.BUILD_NUMBER}"
    }
    stages{
        stage("git checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/gopi720/sailor1.git'
            }
        }
        stage("build"){
            steps{
                sh 'mvn clean verify'
            }
        }
        stage("build docker image"){
            steps{
                sh 'docker image build -t ${image_name}:${env.image_tag} .'
            }
        }
        stage("log in  dockerhub"){
            steps{
                script{
                    withCredentials([string(credentialsId: 'username1', variable: 'username'), string(credentialsId: 'password1', variable: 'password')]) {
                        sh 'docker login -u ${username} -p ${password}'
                    }
                }
            }
        }
        stage("docker push"){
            steps{
                sh 'docker push ${image_name}:${image_tag}'
            }
        }
    }
}