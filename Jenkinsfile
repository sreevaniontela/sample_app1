pipeline{
    agent any 
    tools{
        maven 'maven1'
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
                sh 'docker image build -t gopi1996/speed:4.0 .'
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
                sh 'docker push gopi1996/speed:4.0'
            }
        }
    }
}