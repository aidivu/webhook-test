node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for MSBuild'  type: 'hudson.plugins.sonar.MsBuildSQRunnerInstallation'
  
    withSonarQubeEnv() {
      sh "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"aidivu_webhook-test\""
      sh "dotnet build"
      sh "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
