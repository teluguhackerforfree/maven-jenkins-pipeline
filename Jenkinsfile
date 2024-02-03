pipeline {
  agent any
  tools {
        maven "Maven 3.6.3" 
   }

  stages {
      stage('clone repo') {
            steps {
              git branch: 'main', url: 'https://github.com/devopseng129/maven-jenkins-pipeline.git'
            }
      }
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }  
       }
      stage('Test Maven - JUnit') {
            steps {
              sh "mvn test"
            }
            post{
              always{
                junit 'target/surefire-reports/*.xml'
              }
            }
        }
        

     }
}
