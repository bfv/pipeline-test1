pipeline {
    agent any

    stages {
        stage('Setup') {
            paralell(
                'checkout_framework': {
                    echo 'git checkout bfvlib'    
                },
                'checkout_application': {
                    echo 'git checkout application'
                }
            )
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
