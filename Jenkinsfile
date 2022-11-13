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
                    sshPublisher(publishers: [sshPublisherDesc(configName: 'remote', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'cp index.php index2.php', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'index.php')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                }
            }
        }
    }

}