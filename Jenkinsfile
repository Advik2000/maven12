pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/mymaven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '46120e0c-a952-477d-84d1-8beef00e0ff5', path: '', url: 'http://172.31.3.162:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '46120e0c-a952-477d-84d1-8beef00e0ff5', path: '', url: 'http://172.31.13.52:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }

