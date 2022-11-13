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
                    sshPublisher(publishers: [sshPublisherDesc(configName: 'remote', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                }
            }
        }
    }

}