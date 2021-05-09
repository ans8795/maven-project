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
    
     stage ("build maven and sonarqube analysis")
     {
      steps {
              withSonarQubeEnv('sonarqubenew') {
                 withMaven(jdk: 'JAVA', maven: 'MVN') {
                sh 'mvn clean sonar:sonar package'
              }
            }
     }
     }

 }
 }

