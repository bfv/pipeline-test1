pipeline {

    agent any

    stages {
        stage('Setup') {
            steps {
                parallel(
                    'checkout_framework': {
                        echo 'git checkout bfvlib'
                        dir('src/bfvlib') {
                            git url: 'https://github.com/bfv/bfvlib.git'              
                        }
                    },
                    'checkout_application': {
                        echo 'git checkout application'
                    }
                )
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
