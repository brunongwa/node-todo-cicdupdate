pipeline {
    agent any

    stages{
        stage('Code'){
            steps{
            git url: 'https://github.com/brunongwa/node-todo-cicdupdate.git', branch: 'master'
           }

        }
        stage('Build'){
            steps{
                sh 'docker build -t brunongwa/nodetodo1:latest .'
            }
        }
        stage('Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh 'docker push  brunongwa/nodetodo1:latest'
                }
            }
        }
    }
}
