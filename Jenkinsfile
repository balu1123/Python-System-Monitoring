pipeline {
    agent any
    tools{
        jdk  'jdk11'
        maven  'maven'
    }    
    
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', changelog: false, credentialsId: '15fb69c3-3460-4d51-bd07-2b0545fa5151', poll: false, url: 'https://github.com/jaiswaladi246/Shopping-Cart.git'
            }
        }

        stage('COMPILE') {
            steps {
                sh "mvn clean compile -DskipTests=true"
            }
        }

        stage("Sonarqube Analysis "){
            steps{
                withSonarQubeEnv('sonar-server') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner 
                    -Dsonar.projectName=Python-system-monitor \
                    -Dsonar.projectKey=Python-System-monitor '''
                }
            }
        }
    }
}        