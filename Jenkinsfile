pipeline {

    agent any

    stages {
        stage('checkout repos') {
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
                        dir('src/app1') {
                            git url: 'https://github.com/bfv/app1.git'              
                        }
                    }
                )
            }
        }
        stage('build dbs') {

        }
        stage('compile') {
            steps {
                echo 'Building..'
            }
        }
        stage('test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
