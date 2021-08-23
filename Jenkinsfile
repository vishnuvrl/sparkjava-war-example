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
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("Deploy-Dev"){
            steps{
              sshagent(['tomcat-new']) {
                  sh """
                    scp -o StrictHostKeyChecking=no target/myweb.war ubuntu@172.31.38.19:/opt/tomcat9/webapps/
                    ssh ubuntu@172.31.38.19 /opt/tomcat9/bin/shutdown.sh
                    ssh ubuntu@172.31.38.19 /opt/tomcat9/bin/startup.sh
                  """
    
              }
            }
        }
    }
}
