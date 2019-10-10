node {
  def mvnHome
  stage ('preparation') {
    git 'https://github.com/FrancoBobadilla/IngSoft3_Bobadilla'
    mvnHome = tool 'M3'
  }
  stage ('compile') {
    withEnv (["MVN_HOME=$mvnHome"]) {
      dir ('trabajo-practico-03/payroll/server') {
        if (isUnix()) {
          sh '"$MVN_HOME/bin/mvn" clean package'
        } else {
          bat (/"%MVN_HOME%\bin\mvn" clean package/)
        }
      }
    }  
  }
  stage ('result') {
    archiveArtifacts '**/target/*.jar'
  }
}
