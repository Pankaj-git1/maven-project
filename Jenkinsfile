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
      withMaven(jdk: 'Local_Java',maven: 'Local_Maven') {
     sh 'mvn compile'
      }
}
  } 
    
    }
}
