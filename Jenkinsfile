pipeline
{
agent any
stages
{
stage('Down load the code from SCM')
  {
    steps
{
git branch: 'master', url: 'https://github.com/Pankaj-git1/maven-project.git'
}
}

  stage('compile the code')
  {
    steps
    {
      withMaven(jdk: 'Local_Java', maven: 'Local_Maven') 
	  {
		  withSonarQubeEnv(credentialsId: 'jenkinssonarqube', installationName: 'sonar')
		  {
          sh 'mvn sonar:sonar compile'
      }
}
  } 
  }
	stage('Test the code')
  {
    steps
    {
      withMaven(jdk: 'Local_Java', maven: 'Local_Maven') 
	  {
      sh 'mvn test'
      }
}
  } 
	stage('build')
  {
    steps
    {
      withMaven(jdk: 'Local_Java', maven: 'Local_Maven') 
	  {
      sh 'mvn package'
      }
}
  } 
	
	stage('Deployment')
  {
    steps
    {
      sshagent(['tomcat1']) {
      sh 'scp -o StrictHostKeychecking=no */target/*.war ec2-user@3.83.121.64:/var/lib/tomcat/webapps '
      }
      }
}
	
   
	
	
	
   } 
   }
