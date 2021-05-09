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
    stage ("build")
     {
      steps{
          withMaven(jdk: 'JAVA', maven: 'MVN') {
          sh 'mvn package'
           }
           }    
     }  
     stage ("sonarqube analysis")
     {
      steps {
              withSonarQubeEnv('sonarqubenew') {
                sh 'mvn clean package sonar:sonar'
              }
            }
     }  

 }
 }

