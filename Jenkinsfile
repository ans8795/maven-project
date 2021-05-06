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
     stage ("tomcat dev deployment")
     {
      steps{
         sshagent(['deploytomcat']) {
          sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@15.206.81.60:/var/lib/tomcat/webapps'
                  }
           }    
     }  

 }
 }

