pipeline
{

agent any
stages
{
   stage ("scm checkout")
     {
     steps{
          git branch: 'master', url: 'https://github.com/ans8795/maven-project.git'
          }
     } 
   
     stage ("sonar")
     {
      steps{
          withSonarQubeEnv('sonarqube') {
             withMaven(jdk: 'JAVA', maven: 'MVN') {
                sh 'mvn clean package sonar:sonar'
                  }
           }    
     }  
     }

 }
 }

