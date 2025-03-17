pipeline
{
    agent any
    stages
    {
        stage('Continuous Download')
        {
    steps
    {
        git 'https://github.com/IntelliqDevops/maven.git'
    }
}
stage('Continuous Build') 
{
steps
{
    sh 'mvn package'
}
}
stage('Continuous Deployment')
{
steps
{
    deploy adapters: [tomcat9(credentialsId: 'c34b2b9f-617d-4b25-9164-210062ef8a2b', path: '', url: 'http://172.31.11.106:8080')], contextPath: 'test', onFailure: false, war: '**/*.war'
}
}
stage('Continuous Testing')
{
steps
{
  git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
  sh 'java -jar //home/ubuntu/.jenkins/workspace/declarative/testing.jar'
}
}
stage('Continuous Delivery')
{
steps
{
    deploy adapters: [tomcat9(credentialsId: '0800d8de-3cef-48e2-9316-11e29ceaca20', path: '', url: 'http://172.31.7.189:8080')], contextPath: 'prod', onFailure: false, war: '**/*.war'
}
}
    }
}
