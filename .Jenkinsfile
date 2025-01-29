pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scmGit(
                        branches: [[name: '*/main']],
                        userRemoteConfigs: [[
                            url: 'https://github.com/JustinGeorgeJoseph/GithubActionsTest.git', // Use SSH or HTTPS
                            credentialsId: 'justin_george_joseph' // Set this up in Jenkins
                        ]]
                    )
                }
            }
        }
    }
}
