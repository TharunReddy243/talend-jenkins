pipeline {
 agent any
 environment {
   JAVA_HOME = "C:\\Program Files\\Java\\jdk-17"
   TALEND_CLI = "C:\\Talend\\Talend-Studio-win-x86_64"
   JOB_NAME = "CustomerLoggerJob"
 }
 parameters {
	string(name: 'CSV_FILE_PATH', defaultValue: 'C:/Users/vamsh/OneDrive/Desktop/Talend/customers.csv')
 }
 stages {
   stage('Checkout') {
     steps {
       git branch: 'main',
           url: 'https://github.com/TharunReddy243/talend-jenkins.git'
     }
   }
   stage('Unzip Job') {
     steps {
       bat 'powershell -Command "Expand-Archive -Force CustomerLoggerJob_0.1.zip .\\job2"'
     }
   }
   stage('Run Talend Job') {
     steps {
       bat '''
       cd job2\\CustomerLoggerJob_0.1
       call CustomerLoggerJob_run.bat --context=Default --context_param CSV_FILE_PATH=%CSV_FILE_PATH%
       '''
     }
   }
 }
}
