pipeline {
    agent any

    tools {
        maven 'Maven 3.9.6'   // Exact name as per Jenkins Global Tool Config
        jdk 'JDK 17'          // Exact name as per Jenkins Global Tool Config
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
