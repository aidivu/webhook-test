node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for MSBuild' 
    sh "uname -a"
    sh "lsb_release -a"
    sh "cat /etc/*release"
    sh "cat /etc/issue"
    sh "cat /proc/version"
    withSonarQubeEnv() {
      sh "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"aidivu_webhook-test\""
      sh "dotnet build"
      sh "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
