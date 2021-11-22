node('master') 
{
stage('ContinousDownload')
    {
    git 'https://github.com/intelliqittrainings/maven.git'
    } 
stage('ContinousBuild')
    {
    sh label:'', script: 'mvn package'
    }
stage('ContinousDeployment')
   
 {
    sh label:'', script: 'scp  /home/ubuntu/.jenkins/workspace/scrpitedpipeline/webapp/target/webapp.war    ubuntu@172.31.8.55:/var/lib/tomcat8/webapps/testapp.war'        
    }
stage('ContinousTesting')
    {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'    
    sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/scrpitedpipeline/testing.jar'
    }
stage('ContinousDelivery')

 {
    sh label:'', script: 'scp  /home/ubuntu/.jenkins/workspace/scrpitedpipeline/webapp/target/webapp.war    ubuntu@172.31.9.253:/var/lib/tomcat8/webapps/prodapp.war'
    }
    
}


