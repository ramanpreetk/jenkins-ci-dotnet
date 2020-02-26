pipeline {
agent any

environment {
   PATH = "C:\\Windows\\System32"
   def msbuild = tool name: 'MSBuild', type: 'hudson.plugins.msbuild.MsBuildInstallation'
}

stages {
stage ('Checkout') {
            steps {
                 withCredentials([usernamePassword(credentialsId: 'cicdpipeline', passwordVariable: 'pass', usernameVariable: 'user')]) {
                    git "https://github.com/ramanpreetk/jenkins-ci-dotnet.git"
                 }
            }
}
stage ('Restore Packages') {     
         steps {
             bat '"C:\\Program Files\\dotnet\\dotnet.exe" restore "src\\MyWindowsService\\MyWindowsService.sln" ' 
          }
        }
// stage('Clean') {
//       steps {
//             bat '"C:\\Program Files\\dotnet\\dotnet.exe" clean'
//        }
//     }
stage('Build') {
     steps {
            bat "${msbuild} src\\MyWindowsService\\MyWindowsService.sln"
      }
   }
 }
}