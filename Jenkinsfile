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
              deploy adapters: [tomcat9(credentialsId: '78aff9f7-ec4b-41e4-abaf-7b0e4a7acd9c', path: '', url: 'http://172.31.0.169:8080')], contextPath: 'testapp', war: '**/*.war'
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
             deploy adapters: [tomcat9(credentialsId: '78aff9f7-ec4b-41e4-abaf-7b0e4a7acd9c', path: '', url: 'http://172.31.4.168:8080')], contextPath: 'prodapp', war: '**/*.war'
          }
      }  
    }
    
}
