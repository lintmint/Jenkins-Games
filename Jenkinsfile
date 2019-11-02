pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                lock('lock1') {
                echo 'sleeping 30'
                sleep(30)
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                lock('lock1') {
                    echo 'sleeping 30'
                    sleep(30)
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
