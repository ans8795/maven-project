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
   stage ("compile source code")
     {
      steps{
          withMaven(jdk: 'JAVA', maven: 'MVN') {
          sh 'mvn compile'
           }
           }    
     }
    stage ("test")
     {
      steps{
          withMaven(jdk: 'JAVA', maven: 'MVN') {
          sh 'mvn test'
           }
           }    
     } 
    stage ("build")
     {
      steps{
          withMaven(jdk: 'JAVA', maven: 'MVN') {
          sh 'mvn package'
           }
           }    
     }  
     stage ("sonar")
     {
      steps{
          withSonarQubeEnv('sonar') {
                sh 'mvn clean package sonar:sonar'
                  }
           }    
     }  

 }
 }

