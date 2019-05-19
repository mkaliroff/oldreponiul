pipeline {
    //Use the following docker image to run your dotnet app.
    agent { docker { image 'mcr.microsoft.com/dotnet/core/sdk:2.2' } }
    environment {HOME = '/tmp'} 
    stages {
    // Get some code from a GitHub repository
    stage('Git') {
      steps{
          git 'https://github.com/mkaliroff/ISL.git'
      }
   }
    stage('Dotnet Restore'){
        steps{
        sh "dotnet restore"
        }
    }
    
   stage('Build'){
          steps{
              echo "First Build"
               sh "dotnet build"
               }
    }
    stage('Run Tests'){
          steps{
               sh "dotnet test"
              junit "/*/MVC5_projTests/Controllers/HomeControllerTests.cs"
          }
    }
}
}
