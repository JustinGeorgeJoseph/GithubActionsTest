pipeline {
    agent any

    environment {
        ANDROID_HOME = "/Users/justingeorge/Library/Android"
        PATH = "$ANDROID_HOME/sdk/cmdline-tools/latest/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/JustinGeorgeJoseph/GithubActionsTest.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh './gradlew dependencies'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew assembleDebug assembleAndroidTest'
            }
        }

        stage('Start Emulator') {
            steps {
                script {
                    sh 'echo no | avdmanager create avd -n test -k "system-images;android-33;google_apis;x86_64"'
                    sh 'emulator -avd test -no-window -no-audio -no-boot-anim &'
                    sh './wait-for-emulator.sh'  // You might need to create a script to wait for the emulator to be ready.
                }
            }
        }

        stage('Run Tests') {
            steps {
                sh './gradlew connectedAndroidTest'
            }
        }

        stage('Publish Results') {
            steps {
                junit '**/build/test-results/**/*.xml'
            }
        }
    }

    post {
        always {
            sh 'adb emu kill'  // Clean up the emulator after the test run
        }
    }
}
