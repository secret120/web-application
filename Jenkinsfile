Skip to content
Search or jump to…
Pull requests
Issues
Marketplace
Explore
 
@secret120 
secret120
/
web-application
1
0
0
Code
Issues
Pull requests
Actions
Projects
Wiki
Security
Insights
Settings
web-application/JenkinsfileJuly2021
@devopstrainingblr
devopstrainingblr Rename JenkinsfileJul to JenkinsfileJuly2021
Latest commit dad0d2b 9 days ago
 History
 1 contributor
50 lines (37 sloc)  1.16 KB
  
node{

 def mavenHome = tool name: "maven3.8.2"
 
       echo "GitHub BranhName ${env.BRANCH_NAME}"
       echo "Jenkins Job Number ${env.BUILD_NUMBER}"
       echo "Jenkins Node Name ${env.NODE_NAME}"
  
       echo "Jenkins Home ${env.JENKINS_HOME}"
       echo "Jenkins URL ${env.JENKINS_URL}"
       echo "JOB Name ${env.JOB_NAME}"

 stage('CheckOutCode')
 {
 git branch: 'development', credentialsId: '12993250-1ff3-40a0-9978-794e74dcf712', url: 'https://github.com/MithunTechnologiesDevOps/maven-web-application.git'
 }
 
 stage('Build')
 {
  sh "${mavenHome}/bin/mvn clean package"
 }

 stage('SonarQubeReport'){
 sh "${mavenHome}/bin/mvn clean sonar:sonar"
 }
 
 /*
 stage('UploadArtifactIntoNexus'){
 sh "${mavenHome}/bin/mvn clean deploy"
 }
 
 stage('DeployAppIntoTomcatServer')
 {
 sshagent(['c7a7b3d8-55f0-4f83-9e81-d56c154cc647']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@15.206.90.6:/opt/apache-tomcat-9.0.52/webapps/"
 }
 }
 
 */
 
 stage('SendEmailNotification'){
   emailext body: '''Build is over !!

   Regards,
   Mithun Technologies,
   9980923226''', subject: 'Build Over... !!', to: 'devopstrainingblr@gmail.com'
 }
 
 
}
© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
Loading complete
