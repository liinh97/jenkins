pipeline {

    agent any
    stages {
        stage('Clone') {
            steps{
                git 'https://github.com/liinh97/jenkins.git'
            }
        }

        stage('SSH server'){
            steps{
                sshagent(['aws-remote']) {
                    sh 'ssh -o StrictHostKeyChecking=no -l root 13.212.150.79 touch test.txt'
                }
            }
        }
    }

}