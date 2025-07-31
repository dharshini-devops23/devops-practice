pipeline {
    agent any

    tools {
        maven 'Maven' // Replace with your actual Maven install name
        jdk 'JDK-11'  // Replace with your actual JDK install name
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/dharshini-devops23/devops-practice.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                SONARQUBE_SCANNER_PARAMS = "-Dsonar.projectKey=devops-practice -Dsonar.projectName=devops-practice"
            }
            steps {
                withSonarQubeEnv('MySonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
