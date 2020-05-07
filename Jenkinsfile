def sourceDir = "../../src"
def buidDir = "../../build"
    
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
                            bat "ant createdb -file ${sourceDir}/bfvlib/build.xml -DDLC=c:/dlc/117 -Dsrcdir=${sourceDir}/bfvlib -Dbuilddir=${buildDir}"
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
                bat "ant compile -f src/bfvlib/build.xml -DDLC=c:/dlc/117 -Dbuilddir=${buildDir}"
                bat "ant package -f src/bfvlib/build.xml -DDLC=c:/dlc/117 -Dbuilddir=${buildDir}"
            }
            post {
                success {
                    archiveArtifacts artifacts: 'src/build/bfvlib.pl', fingerprint: true
                }
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
