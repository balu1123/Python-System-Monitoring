pipeline {
    agent any
    tools{
        jdk  'jdk11'
        maven  'maven'
    }    

    environment{
        SCANNER_HOME= tool 'sonar-scanner'
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/balu1123/Python-System-Monitoring.git'
            }
        }

        stage('clean workspace'){
            steps{
                cleanWs()
            }
        }    
        
        stage('Sonarqube Analysis'){
            steps{
                withSonarQubeEnv('sonar-scanner') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner 
                    -Dsonar.projectName=Python-system-monitor \
                    -Dsonar.projectKey=Python-System-monitor '''
                }
            }
        }
    }
}        