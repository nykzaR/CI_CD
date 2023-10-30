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

        stage('Execute the Script') {
            steps {
                sh 'packer validate az.json && packer build az.json'
            }
        }
    }
}    