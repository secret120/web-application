node{
def mavenHome = tool name: "maven3.8.2"
stage('git clone'){
git branch: 'development', credentialsId: '9aaf7227-6341-4a04-90f0-402b9f9cb51a', url: 'https://github.com/secret120/web-application.git'
}
stage('build'){
sh "${mavenHome}/bin/mvn clean package"
}
stage('SonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('uploadartifactintonexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}
stage('DeployAppIntoTomcatServer')
{
sshagent(['9902fef4-3530-4df8-95ef-cd7b8797bce7']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.2.126.8:/opt/apache-tomcat-9.0.52/webapps"
}
}
stage('SendEmailNotification'){
emailext body: '''Build is over

Thanks,
maniSwathi''', subject: 'Build over', to: 'melissa123.powell@gmail.com'
}
}
