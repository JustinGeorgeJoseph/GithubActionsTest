pipeline {
    agent any

    stages {

           stage('Print something') {
                steps {
                    script {
                                            echo "✅ Start working."

                    }
                }
            }


        stage('Checkout -1') {
            steps {
                script {
                    checkout scmGit(
                        branches: [[name: '*/main']],
                        userRemoteConfigs: [[
                            url: 'git@github.com:JustinGeorgeJoseph/GithubActionsTest.git', // Use SSH or HTTPS
                            credentialsId: 'justin_george_joseph' // Set this up in Jenkins
                        ]]
                    )
                    echo "✅ Checkout successful! Repository cloned."
                }
            }
        }
    }
}
