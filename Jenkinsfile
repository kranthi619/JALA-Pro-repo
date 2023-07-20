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
      sh 'mvn clean package'
    }
 }
  
  stage('publishing reports using HTML') {
     steps {
     echo " this is HTML reports"
     publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/project1/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
   }
  }
 } 
}
