pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('tesr') {
      parallel {
        stage('unit') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('functionnal') {
          steps {
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('deployement') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o/var/aspnet'
      }
    }

  }
}