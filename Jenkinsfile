node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for MSBuild'
    withSonarQubeEnv() {
      bat "dotnet ${msbuildHome}\\SonarScanner.MSBuild.dll begin /k:\"dummy-test-org_testdotnet\""
      bat "dotnet build ."
      bat "dotnet ${msbuildHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
