pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Om11013/Jenkins-Pipeline-Demo.git'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'docker build -t poonjaniom895/dockerpipeline .'
                    } else {
                        bat 'docker build -t poonjaniom895/dockerpipeline .'
                    }
                }
            }
        }

        stage('Docker Push') {
            steps {
                script {
                    def username = 'poonjaniom895'
                    def password = '**********'

                    if (isUnix()) {
                        sh "echo ${password} | docker login -u ${username} --password-stdin"
                        sh 'docker push poonjaniom895/dockerpipeline'
                        sh 'docker logout'
                    } else {
                        bat "echo %password% | docker login -u %username% --password-stdin"
                        bat 'docker push poonjaniom895/dockerpipeline'
                        bat 'docker logout'
                    }
                }
            }
        }
    }
}