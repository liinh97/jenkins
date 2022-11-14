pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/liinh97/jenkins.git'
            }
        }

        stage('SSH server') {
            steps {
                sshagent(['aws-remote']) {
                    sshPublisher(publishers: [sshPublisherDesc(configName: 'remote', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'cp var/www/html/* /var/www/html', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/www/html', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                }
            }
        }

        stage('Remote server') {
            steps {
                sshagent(['ubuntu-remote']) {
                    sh 'ssh -o StrictHostKeyChecking=no -l root 54.169.119.11 cat .bashrc'
                }
            }
        }
    }
}
