pipeline {
 agent any

 tools {
   maven 'M2_HOME'
   }

 stages {
  stage('git checkout') {
    steps {
       echo 'check out the source code from git hub'
       git 'https://github.com/kranthi619/finance-pro.git'
   }
 }

  stage('packaging the application usimg maven ') {
    steps {
      echo ' packaging the application using maven '
      sh 'mvn cleane package'
    }
 }

  stage('publishing reports using HTML') {
     steps {
     echo " this is HTML reports"
     publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/project1/targets/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
   }
 }
  
 stage('creation of docker image') {
   steps {
   echo 'inform me that docker images is created '
   sh 'docker build -t kranthi619/project1:latest .'
   }
 }
  
 stage('docker hub login') {
   steps {
   withCredentials([usernamePassword(credentialsId: 'docker-hub-cre', passwordVariable: 'docker_passwd', usernameVariable: 'docker_usr')]) {
   sh 'docker login -u ${env.docker_usr} -p ${env.docker_passwd}'
   }
  }
 }
  
 stage('pushing image ro docker hub') {
   steps {
   sh 'docker push kranthi619/project1:latest'
    }
  }
}
}
