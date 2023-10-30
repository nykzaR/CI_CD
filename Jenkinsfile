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
        stage ('Check 'cli-s' directory exists') 
        {
            steps {
                script {
                    if (fileExists('${WORKSPACE}/cli-s/')) 
                    {
                        sh "cd cli-s"
                    }
                    else
                    {
                        sh 'git clone https://github.com/Prozects/cli-s.git && cd cli-s'
                    }
                }
            }
        }
        stage('Execute the Script') {
            steps {
                sh 'packer validate az.json && packer build az.json'
            }
        }
    }
}    