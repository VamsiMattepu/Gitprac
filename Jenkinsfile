node('master') 
{
  stage('Continousdownload_Master') 
  {
   git 'https://github.com/intelliqittrainings/maven.git'
  }
  stage('ContinousBuild_Master') 
  {
   sh 'mvn package'
  }
  stage('ContinousDeploy_Master') 
  {
   deploy adapters: [tomcat9(credentialsId: '457d8081-2137-478a-8c21-dc1fa233816e', path: '', url: 'http://172.31.36.186:8080')], contextPath: 'qqapp', war: '**\\*.war'
  }
  stage('ContinousTesting_Master') 
  {
   git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
   sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
  }
  stage('ContinousDelivery_Master') 
  {
   deploy adapters: [tomcat9(credentialsId: '457d8081-2137-478a-8c21-dc1fa233816e', path: '', url: 'http://172.31.38.171:8080')], contextPath: 'ppapp', war: '**\\*.war'
  }
}
