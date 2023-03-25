node('nodes') 

{

def mavenHome= tool name: "Maven-3.9.1"
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '4', artifactNumToKeepStr: '5', daysToKeepStr: '30', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])

stage('checkout')
{
git branch: 'development', credentialsId: 'cd765832-ec7e-44c1-ae90-0c9f8f1e9223', url: 'https://github.com/vamsi113113/Maven-Web-Application.git'
}
stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"
}
/*stage('executeSonarcube')
{
sh "${mavenHome}/bin/mvn sonar:sonar"     
}
stage ('TomcatDeploy')
{
sshagent(['e74d0c32-3fa4-4303-84e7-41cb1f34a569']) 
{
}    
}*/
stage('email notification')
{
 emailext body: '''Build is done 

Regards,
Vamsidhar Reddy.''', subject: 'Build is done', to: 'rachuri113@gmail.com'   
}
}
