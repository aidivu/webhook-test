pipeline {
  stages {
    stage('Build') {
      steps {
        script {
          def msbuild = tool name: 'MSBuild', type: 'hudson.plugins.msbuild.MsBuildInstallation'
          bat "${msbuild} RealWorldMinimalApi/RealWorldMinimalApi.sln"
        } 
      } 
    } 
  } 
} 
