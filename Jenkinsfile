node ('node1')
{	

def mavenHome = tool name: "maven3.8.4"	
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * * ')])])

    	stage('CheckoutCode')
	{
	git branch: 'development', credentialsId: 'c116bb27-dffb-4587-8a20-eaea162ec57a', url: 'https://github.com/samba7989893459/maven-web-application.git'
	}
    
   	 stage('Build')
	{
	sh "${mavenHome}/bin/mvn clean package"
	}
	
    	stage('ExecuteSonarQubeReport')
	{
	sh "${mavenHome}/bin/mvn sonar:sonar"
	}
	/*
    	stage('UploadArtifactIntoNexus')
	{
	sh "${mavenHome}/bin/mvn deploy"
	}

    	stage('DepolyAppIntoTomcat')
	{
	sshagent(['25499363-b890-49ce-aed5-458082dec390']) 
	{
	sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.6.36.182:/opt/apache-tomcat-9.0.58/webapps/"
	}
	}
	
	stage('SendEmailNotification')
	{
	mail bcc: '', body: '''Build Over,

	Regards,
	Samba Tech
	7989893459''', cc: 'samba81424.sr@gmail.com', from: '', replyTo: '', subject: 'Build Over', to: 'samba7989.sr@gmail.com'
	}
	
	*/
}
