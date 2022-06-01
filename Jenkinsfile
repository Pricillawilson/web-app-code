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
            }
        }
    }
}