node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv('sonar') {
      sh "./gradlew sonar"
    }
  }
}
