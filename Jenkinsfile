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
        stage('ContinuousDeployment')
        {
            steps
            {
                sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.31.15:/var/lib/tomcat8/webapps/testwebapp.war'
            }
            
        }
    }   
}
