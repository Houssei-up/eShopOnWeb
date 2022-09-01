pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'dotnet build eShopOnWeb.sln', returnStatus: true, returnStdout: true)
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Fonctional') {
          steps {
            sh 'dotnet test tests/FonctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb -sln -o C:\\Users\\houss\\Desktop\\COURS2'
      }
    }

  }
}