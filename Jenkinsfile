pipeline {
agent any

environment {
dotnet = "C:/Program%20Files/dotnet/dotnet.exe"
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
             bat "C:\\Program%20Files\\dotnet\\dotnet.exe restore --configfile NuGet.Config"
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