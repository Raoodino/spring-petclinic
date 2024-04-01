node {
  stage('SCM') {
    checkout scm
  }

  stage('Build with Gradle') {
    steps {
      script {
        // Builds the petclinic.jar
        sh './gradlew clean build'
        // The build artifact (petclinic.jar) should now be in the build/libs directory
      }
    }
  }
  

  stage('SonarQube Analysis') {
    withSonarQubeEnv('sonar') {
      // Use the container name as the hostname for SonarQube server
      sh "./gradlew sonar"
    }
  }


  
  stage('Execute Jar') {
    steps {
      script {
        // Adjust the jar name as needed
        sh 'java -jar build/libs/spring-petclinic-3.2.0.jar &'
      }
    }
  }
}
