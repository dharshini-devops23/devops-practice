pipeline {
    agent any

    tools {
        jdk 'JDK 17'              // ✅ Use exactly what Jenkins recognizes
        maven 'Maven 3.9.6'
    }

    environment {
        SONARQUBE_SERVER = 'MySonarQube' // Replace with exact SonarQube server name
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/dharshini-devops23/devops-practice.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${env.SONARQUBE_SERVER}") {
                    bat 'mvn sonar:sonar -Dsonar.projectKey=devops-practice'
                }
            }
        }
    }
}
