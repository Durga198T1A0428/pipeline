

node('built-in')
{
    stage('continuous downloading')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    
    }
    stage('continuous build')
    {
        sh 'mvn package'
    }
    stage('continuous deployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'a43c3bfd-6b92-4266-b2af-01f45437a998', path: '', url: 'http://52.37.125.97:8080')], contextPath: 'test', war: '**/*.war'
    }
    stage('continuous testing')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/scripted/testing.jar'
    }
    stage('continuous build')
    {
        deploy adapters: [tomcat9(credentialsId: 'a43c3bfd-6b92-4266-b2af-01f45437a998', path: '', url: 'http://54.70.229.5:8080')], contextPath: 'prod', war: '**/*.war'
    }
    
}
