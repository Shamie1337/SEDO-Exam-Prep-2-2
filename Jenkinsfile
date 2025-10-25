pipeline {
  
  agent any
  triggers {
    githubPush()
  }

  stages {
    stage('Checkout') {
      when { branch 'main' }
      steps {
        checkout scm
      }
    }
    stage('Setup .NET') {
      when { branch 'main' }
      steps {
        sh 'dotnet --version'
      }
    }
    stage('Restore dependencies') {
      when { branch 'main' }
      steps {
        sh 'dotnet restore'
      }
    }
    stage('Build') {
      when { branch 'main' }
      steps {
        sh 'dotnet build --no-restore'
      }
    }
    stage('Test') {
      when { branch 'main' }
      steps {
        sh 'dotnet test --no-build --verbosity normal'
      }
    }
  }
}
