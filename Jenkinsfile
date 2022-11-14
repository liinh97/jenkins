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
                    sh 'ssh -o StrictHostKeyChecking=no -l root 54.169.119.11 sudo apt-get install -y php8.1-cli php8.1-common php8.1-mysql php8.1-zip php8.1-gd php8.1-mbstring php8.1-curl php8.1-xml php8.1-bcmath'
                    sh 'ssh -o StrictHostKeyChecking=no -l root 54.169.119.11 wget -O phpunit https://phar.phpunit.de/phpunit-8.phar'
                    sh 'ssh -o StrictHostKeyChecking=no -l root 54.169.119.11 chmod +x phpunit'
                }
            }
        }
    }
}
