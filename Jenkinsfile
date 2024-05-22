pipeline {
    agent any
    tools{
        maven 'maven'
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
            steps{
                deploy adapters: [tomcat9(credentialsId: '2268088b-9150-40c9-abe9-831ceabd8c67', path: '', url: 'http://3.127.223.253:8081/')], contextPath: null, war: '**/target/*.war'
            }
        }
        }
    }
}