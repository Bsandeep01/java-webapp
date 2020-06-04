pipeline{
    agent any 
    tools{
        maven 'maven'
        jdk 'java'
    }
    stages {
        stage ('Git checkout') {
            steps {
                git 'https://github.com/Bsandeep01/hello-world.git'
            }
        }
        stage ('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage ('send artifacts over ssh') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'Amz-Ans-Docker', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', remoteDirectorySDF: false, removePrefix: '/webapp/target', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
} 
