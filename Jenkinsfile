node

{
  def buildNumber= BUILD_NUMBER
  def mavenHome=tool name: "maven3.6.3"
  
 stage('Checkout')
 {
 	git branch: 'development', credentialsId: 'GitHubCredentials', url: 'https://github.com/Acc-git-class/maven-web-application.git'
 
 }

 



 stage('Build')
 {
 sh  "${mavenHome}/bin/mvn clean package"
 }
 
 stage('ExecuteSoanrQubeReport')
 {
 sh  "${mavenHome}/bin/mvn sonar:sonar"
 }
 
 stage('UploadArtifactintoNexus')
 {
 sh  "${mavenHome}/bin/mvn deploy"
 }
  
 stage('Docker Integration')
 {
 sh "docker build -t geethika609/maven-web-application:${buildNumber} ."
 }
 
 stage('Docker login and push')
 {
 sh "docker login -u geethika609 -p Geethika@609"
 sh "docker push geethika609/maven-web-application:${buildNumber}"
 }
  /*
 stage('DeployAppintoTomcat')
 {
 sshagent(['cd93d61f-2d0f-4c60-8b33-34cf4fa888b0']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.235.132.183:/opt/apache-tomcat-9.0.29/webapps/"
 }
 }

 stage('SendEmailNotification')
 {
 emailext body: '''Build is over..

 Regards,
 Mithun Technologies,
 9980923226.''', subject: 'Build is over', to: 'geethikainfy@gmail.com'
 } */

}
