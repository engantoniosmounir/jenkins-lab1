pipeline {
    agent any

    environment {
        GITHUB_TOKEN = credentials('github-token')
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Check PHP Version') {
            steps {
                echo 'Checking PHP version...'
                sh 'php -v'
            }
        }

        stage('Check PHPUnit Version') {
            steps {
                echo 'Checking PHPUnit version...'
                sh 'phpunit --version'
            }
        }

        stage('Run Unit Tests') {
            steps {
                echo 'Running PHPUnit tests...'
                sh 'phpunit'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded. All tests passed.'
        }

        failure {
            echo 'Build failed. One or more tests failed.'
        }
    }
}