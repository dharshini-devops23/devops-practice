pipeline {
    agent any

    tools {
        sonarQubeScanner 'SonarScanner'  // Use the exact name from Jenkins
    }

    environment {
        SONARQUBE_ENV = 'MySonarQube'   // Use the SonarQube name from Jenkins config
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/dharshini-devops23/devops-practice.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${env.SONARQUBE_ENV}") {
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 2, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
