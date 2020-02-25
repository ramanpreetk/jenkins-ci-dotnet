pipeline {
agent any

environment {
   // PATH = "C:\\WINDOWS\\SYSTEM32"
   // dotnet = "C:/Program Files/dotnet/dotnet.exe"
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
             bat "dotnet restore --configfile NuGet.Config"
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