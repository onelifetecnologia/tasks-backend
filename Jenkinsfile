pipeline {
    agent any
    stages{
        stage('Build Backend'){
            steps{
                powershell 'mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Tests'){
            steps{
                powershell 'mvn test'
            }
        }
    }
}