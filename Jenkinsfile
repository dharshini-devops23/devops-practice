pipeline {
    agent any

    tools {
        maven 'Maven 3.9.6'
        jdk 'JDK 17'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/dharshini-devops23/devops-practice.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                SONARQUBE_SCANNER_PARAMS = "-Dsonar.projectKey=devops-practice -Dsonar.projectName=devops-practice"
            }
            steps {
                withSonarQubeEnv('SonarScanner') {
                    bat 'mvn sonar:sonar'
                }
            }
        }
    }
}
