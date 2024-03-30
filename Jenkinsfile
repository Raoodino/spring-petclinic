node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
     withSonarQubeEnv('SonarQube') { // Make sure 'SonarQube' matches the name in Jenkins configuration
      // Use the container name as the hostname for SonarQube server
      sh "./gradlew sonarqube -Dsonar.host.url=http://sonarqube:9000"
    }
  }
}
