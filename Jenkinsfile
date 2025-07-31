pipeline {
    agent any

    tools {
        // Make sure this matches the name of SonarScanner in Jenkins > Global Tool Configuration
        sonarScanner 'SonarScanner'
    }

    environment {
        // Optional: If you need to use the token explicitly
        SONAR_TOKEN = credentials('sonar-token') 
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonarQube') {
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
