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
        stage('Executing Script') {
            steps {
                sh 'packer validate .\az.json && packer build .\az.json'
            }
        }
    }
}    