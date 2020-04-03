pipeline {

    agent { label 'win' }

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
                            // sh "ant createdb -file ../../src/bfvlib/build.xml -DDLC=c:/dlc/117 -Dsrcdir=../../src/bfvlib -Ddbdir=."
                            echo 'build framework'
                        }
                    },
                    'application': {
                        dir('dbs/application') {
                            echo 'build application'
                        }
                    }
                )
            }
        }
        stage('compile') {
            steps {
                echo 'test Ant call'
                bat "ant -f src/framework/build.xml -DDLC=c:/dlc/117"
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
