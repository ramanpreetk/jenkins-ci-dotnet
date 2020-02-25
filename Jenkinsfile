pipeline {
agent any

environment {
dotnet = "C:\\Program Files\\dotnet"
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