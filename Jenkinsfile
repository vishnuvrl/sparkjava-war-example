pipeline{
    agent any
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }
    stages{
        stage("Git Ceckout"){
            steps{
                git 'https://github.com/vishnuvrl/sparkjava-war-example'
            }
           
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
            }
           
        }
    }
}
