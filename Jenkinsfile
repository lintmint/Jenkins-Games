pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                lock(lock1) {
                echo 'Building..'
                }
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
