 pipeline {
   agent any
   stages{ 
     stage("Git checkout") {
     steps{
          git 'https://github.com/HemaSahuRathore/java-hello-world-webapp.git'
          }
     }

     stage("Build stage") {
     steps{
           sh 'mvn clean package'
           sh 'mv target/*.war target/myweb.war'
          }
     
     }

     stage("war file deploy"){
     steps{
     sshagent(['Tomcat-Key']) {
        sh "scp -o StrictHostKeyChecking=no target/myweb.war ubuntu@172.31.13.197:/opt/tomcat/webapps"
        }
       }
      }

   }
}
