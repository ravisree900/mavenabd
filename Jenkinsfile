pipeline
{
    agent any
    stages
    {
      stage('continiousDownload')
      {
          steps
          {
              git 'https://github.com/intelliqittrainings/maven.git'
          }
      }  
      stage('continiousBuild')
      {
          steps
          {
              sh 'mvn package'
          }
      }  
}
