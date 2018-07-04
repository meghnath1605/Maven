node('master') 
{
stage('ContinuousDownload') 
{
    git 'https://github.com/selenium-saikrishna/maven.git'
}

stage('ContinuousBuild') 
{
    sh 'mvn package'
}

stage('ContinuousDeployement') 
{
sh 'scp /var/lib/jenkins/workspace/pipeline/webapp/target/webapp.war vagrant@192.168.60.31:/var/lib/tomcat7/webapps/qa.war'
}

stage('ContinuousTesting') 
{
    git 'https://github.com/selenium-saikrishna/TestingOnAWS.git' 
}

stage('ContinuousDelievery') 
{
input message: 'waiting for approval', submitter: 'hari'
sh 'scp /var/lib/jenkins/workspace/pipeline/webapp/target/webapp.war vagrant@192.168.60.32:/var/lib/tomcat7/webapps/prod.war'
}



}
