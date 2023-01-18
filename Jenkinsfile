pipeline{
    agent any
    environment {
        PATH = "$PATH:/usr/share/maven/bin"
    }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/prasanthplavada/MavenJacoco.git'
            }
         }
       stage('mvn clean Package'){
            steps{
                sh 'mvn clean package'
            }
        }
       stage('mvn clean Install'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('mvn test'){
            steps{
                sh 'mvn test'
            }
        }
       stage('SonarQube analysis') {
            steps{
                withSonarQubeEnv('sonarqube-8.3') { 
                sh ''' mvn verify sonar:sonar -Dsonar.login=admin -Dsonar.password=admin'''
                }
                
            }
        }
       
    }
}
