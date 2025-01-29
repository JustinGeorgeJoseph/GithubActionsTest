pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scmGit(
                        branches: [[name: '*/github-lfs-test']],
                        userRemoteConfigs: [[
                            url: 'https://github.com/JustinGeorgeJoseph/GithubActionsTest.git', // Use SSH or HTTPS
                            credentialsId: 'justin_george_joseph' // Set this up in Jenkins
                        ]]
                    )
                    echo "✅ Checkout successful! Repository cloned."
                }
            }
        }
    }
}
