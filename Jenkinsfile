pipeline{
    agent any
    environment{
        PATH = "/opt/apache-maven-3.8.5/bin:$PATH"
    }
    stages{
        stage("Welcome"){
            steps{
                echo 'Hellaloo'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("deploy-dev"){
            steps{
                sshagent(['tomcat-new']){
                    sh """
                        scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@:13.127.76.202/opt/tomcat8/webapps/
                        ssh ec2-user@13.127.76.202 /opt/tomcat8/bin/shutdown.sh
                        ssh ec2-user@13.127.76.202 /opt/tomcat8/bin/startup.sh
                    """
                }
            }
        }
    }
}