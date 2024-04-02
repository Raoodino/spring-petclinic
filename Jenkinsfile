node {
  // environment {
  //       SONAR_HOST_URL = 'http://172.21.0.2:9000'
  //   }
  stage('SCM') {
    checkout scm
  }
  // stage('Build JAR') {
  //       // Assuming you're using Gradle to build the JAR
  //       sh "./gradlew build"
  // }
  stage('SonarQube Analysis') {
    withSonarQubeEnv('sonar') {
      sh "./gradlew sonar -Dsonar.host.url=http://sonarqube:9000"
    }
  }
  // stage('Execute JAR') {
  //     // Execute the JAR file from the Jenkins workspace directory
  //     sh 'java -jar /var/jenkins_home/workspace/test1/build/libs/spring-petclinic-3.2.0.jar'
  // }
}
