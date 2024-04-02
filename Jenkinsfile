pipeline {
  agent any
   environment {
        _git_url = "https://github.com/Raoodino/spring-petclinic.git"
        _git_branch = '*/main'            
    }
    options {
      timeout(time: 1, unit: 'HOURS') 
  }
  tools {
      gradle 'gradle'
      git 'git'
  }
stages {
        stage('Git Checkout') { 
            steps    {
                checkout([$class: 'GitSCM', branches: [[name: "${_git_branch}"]], extensions: [],userRemoteConfigs: [[credentialsId: "", url: "${_git_url}"]]])
            }
        }
        stage('Maven Build') {
            steps    {
                sh '''
                rm -f Jenkinsfile && chmod +x mvnw gradlew
                ./gradlew build
                '''
            }
        }
        stage('SonarQube Analysis') {
            steps    {	
                script {
                	  scannerHome = tool 'sonarqube'
                }					  
                withSonarQubeEnv('sonar') {
                    sh "./gradlew sonar -Dsonar.host.url=http://sonarqube:9000"
			    //sh """${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=${JOB_BASE_NAME} -Dsonar.projectName=${JOB_BASE_NAME} -Dsonar.sources=. """
               }
			 }
        }
  }
}
