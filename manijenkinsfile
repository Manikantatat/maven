node('built-in')
{
   stage('ContinuousDownload') 
   {
       git 'https://github.com/intelliqittrainings/maven.git'    
   }
   stage('ContinuousBuild')
   {
       sh 'mvn package'
   }
   stage('deploy')
   {
       deploy adapters: [tomcat9(credentialsId: 'e0a1097a-b575-479c-9f69-001dcf40a418', path: '', url: 'http://172.31.6.44:8080')], contextPath: 'qaapp', war: '**/*.war'
   }
   stage('testing')
   {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /var/lib/jenkins/workspace/PP/testing.jar'
       
   }
   stage('production')
   {
       deploy adapters: [tomcat9(credentialsId: 'e0a1097a-b575-479c-9f69-001dcf40a418', path: '', url: 'http://172.31.13.167:8080')], contextPath: 'pdapp', war: '**/*.war'
   }
}

