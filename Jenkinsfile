pipeline {

    agent any

    stages {
        stage('checkout repos') {
            steps {
                parallel(
                    'framework': {
                        dir('src/bfvlib') {
                            git url: 'https://github.com/bfv/bfvlib.git'              
                        }
                    },
                    'application': {
                        dir('src/app1') {
                            git url: 'https://github.com/bfv/app1.git'              
                        }
                    }
                )
            }
        }
        stage('build dbs') {
            steps {
                parallel(
                    'framework': {
                        dir('dbs/framework') {

                        }
                    },
                    'application': {
                        dir('dbs/application') {
                            
                        }
                    }
                )
            }
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
