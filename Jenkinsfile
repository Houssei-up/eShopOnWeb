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
            bat(script: 'dotnet test tests/UnitTests', returnStatus: true, returnStdout: true)
          }
        }

        stage('Integration') {
          steps {
            bat(script: 'dotnet test tests/IntegrationTests', returnStatus: true, returnStdout: true)
          }
        }

        stage('Fonctional') {
          steps {
            bat(script: 'dotnet test tests/FonctionalTests', returnStatus: true, returnStdout: true)
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        bat(script: 'dotnet publish eShopOnWeb.sln -o C:\\Users\\houss\\Desktop\\COURS2', returnStatus: true, returnStdout: true)
      }
    }

  }
}