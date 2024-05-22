pipeline {
    agent any
    tools{
        maven ''
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean compile'
                sh 'mvn test'
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "archiving the artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server'){
            
        }
        }
    }
}