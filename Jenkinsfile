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
        stage('Sonar Analisys'){
            environment{
                scannerHome= tool 'SONAR_SCANNER'
            }
            steps{
                withSonarQubeEnv('SONAR_LOCAL'){
                    powershell "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=DeployBack -Dsonar.host.url=http://localhost:9000 -Dsonar.login=85c964bd171214ca14526c00cc0fdfe0354f40b0 -Dsonar.java.binaries=target -Dsonar.covarage.exclusions=**/.mvn/**,**/src/test/**,**/model/**,**Application.java"
                }
            }
        }
    }
}


  