pipeline {
    agent any

    tools {
        maven 'M2_HOME'
    }

    stages {
        stage('git checkout') {
            steps {
                echo 'check out the source code from git hub'
                git 'https://github.com/kranthi619/JALA-Pro-repo.git'
            }
        }

        stage('packaging the application using maven') {
            steps {
                echo 'packaging the application using maven'
                sh 'mvn clean package'
            }
        }

        stage('creation of docker image') {
            steps {
                echo 'inform me that docker images is created'
                sh 'docker build -t kranthi619/project1:latest .'
            }
        }

        stage('docker hub login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerPass', usernameVariable: 'dockerUsr')]) {
                    sh 'docker login -u $dockerUsr -p $dockerPass'
                }
            }
        }

        stage('pushing image to docker hub') {
            steps {
                sh 'docker push kranthi619/project1:latest'
            }
        }
    }
}

       
