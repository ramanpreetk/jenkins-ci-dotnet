pipeline {
agent any

environment {
   PATH = "C:\\Windows\\System32"
}

stages {
stage ('Checkout') {
            steps {
                 withCredentials([usernamePassword(credentialsId: 'cicdpipeline', passwordVariable: 'pass', usernameVariable: 'user')]) {
                    checkout scm
                 }
            }
}
stage ('Restore Packages') {     
         steps {
             bat '"C:\\Program Files\\dotnet\\dotnet.exe" restore "D:\\DevOps Training\\DemoPipeline\\jenkins-ci-dotnet\\src\\MyWindowsService\\MyWindowsService.sln" ' 
          }
        }
stage('Clean') {
      steps {
            bat 'dotnet clean'
       }
    }
stage('Build') {
     steps {
            bat 'dotnet build --configuration Release'
      }
   }
 }
}