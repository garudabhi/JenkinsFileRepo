pipeline {
    agent any
    stages {
        stage('Clean') {
            steps {
                bat 'rmdir /Q /S GitToApache'
            }
        }
        stage('Get Code') {
            steps {
                echo 'Getting Code from Repo'
                bat "git clone https://github.com/garudabhi/GitToApache.git"
            }
        }
        stage('Update File') {
            steps {
                echo 'Updating index.html'
                bat 'echo %date% %time% >> GitToApache/index.html'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying index.html'
                bat returnStdout: true, script: 'copy /Y GitToApache\\index.html D:\\Dev-ops\\Apache24\\htdocs\\index.html'
            }
        }
        stage('Confirm') {
            input {
                message "Complete Deployment ?"
                ok "Yes Please"
                }
            steps {
                echo 'shouldWe'
            }
        }
    }
}