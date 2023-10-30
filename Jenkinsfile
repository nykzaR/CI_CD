pipeline {
    agent { label 'packer' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('VCS') {
            steps {
                git url: 'https://github.com/Prozects/cli-s.git',
                    branch: 'main'
            }
        }
        stage('Configure Azure cli') {
            steps {
                sh 'sudo apt-get update && curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash'
            }
        }
        stage('Execute the Script') {
            steps {
                sh 'packer validate az.json && packer build az.json'
            }
        }
    }
}    