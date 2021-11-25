node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    
     sh ''' 
     wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
     dpkg -i packages-microsoft-prod.deb
    rm packages-microsoft-prod.deb
      '''
    sh '''
     apt-get update; \
     apt-get install -y apt-transport-https && \
     apt-get update && \
     apt-get install -y dotnet-sdk-6.0
    '''
   
    def scannerHome = tool 'SonarScanner for MSBuild' 
  
    withSonarQubeEnv() {
      sh "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"aidivu_webhook-test\""
      sh "dotnet build"
      sh "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
