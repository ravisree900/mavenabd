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
       stage('continiousDeployment')
      {
          steps
          {
              sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.31.15:/var/lib/tomcat8/webapps/testwebapp.war'
          }
      } 
      stage('continiousTesting')
      {
          steps
          {
             git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
             sh '''java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'''
          }
      } 
      stage('continiousDelivery')
      {
          steps
          {
             sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.26.41:/var/lib/tomcat8/webapps/prodwebapp.war'
          }
      }  
    }
    
}
