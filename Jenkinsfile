pipeline {
    agent { label 'packer' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('VCS') {
            steps {
                git url: 'https://github.com/nykzaR/CI_CD.git',
                    branch: 'main'
            }
        }
        stage('Clone the repository') {
            steps {
                sh 'git clone https://github.com/Prozects/cli-s.git && cd cli-s'
            }
        }
        stage('Execute the Script') {
            steps {
                sh 'packer validate az.json && packer build az.json'
            }
        }
    }
}    