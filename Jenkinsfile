node {
  // environment {
  //       SONAR_HOST_URL = 'http://172.21.0.2:9000'
  //   }
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv('sonar') {
      sh "./gradlew sonar -Dsonar.host.url=http://sonarqube:9000"
    }
  }
}
