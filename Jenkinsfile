node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for MSBuild'
    withSonarQubeEnv() {
      sh "dotnet ${msbuildHome}/SonarScanner.MSBuild.dll begin /k:\"dummy-test-org_testdotnet\""
      sh "dotnet build ."
      sh "dotnet ${msbuildHome}/SonarScanner.MSBuild.dll end"
    }
  }
}

