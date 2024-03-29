pipeline {
    agent any

    environment {
        BOT_TOKEN = '6451695822:AAEvuVexMDi5jgKLycHSe_q45vvSFrsp9b8'
        CHAT_ID = '-1002142392049'
    }

    stages {
        stage('Git Checkout') {
            steps {
                echo 'Code checkout.'
                git branch: 'master', url: 'https://github.com/Mony-Ratanak/DevOps-Midterm/'
            }
        }
        stage('Build App') {
            steps {
                echo 'Building...'
                sh "gradle clean build"
            }
        }
        stage('Testing App') {
            steps {
                echo 'Testing...'
                sh "gradle test"
            }
        }
    }

    post {
        success {
            sh '''
                bash scripts/deployment.sh SUCCESS🟢
            '''
        }
        failure {
            sh '''
                bash scripts/deployment.sh FAILED🔴
            '''
        }
    }
}
