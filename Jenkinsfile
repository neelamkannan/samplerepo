node('myslave') 
{
    stage('continuousdownload') 
    {
       git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('continuousbuild') 
    {
       sh 'mvn package'
    }
    stage('continuousDeploy')
    {
        deploy adapters: [tomcat9(credentialsId: '1209377e-4dd4-48c7-9fd1-72ec5b2e8f4b', path: '', url: 'http://172.31.23.186:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuoustesting') 
    {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /home/ubuntu/remote_root/workspace/scriptedpipeline/testing.jar'
    }
    stage('continousdelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '1209377e-4dd4-48c7-9fd1-72ec5b2e8f4b', path: '', url: 'http://172.31.17.135:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
