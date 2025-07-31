pipeline {
    agent any

    tools {
        jdk 'JDK21'              // ✅ Exactly match JDK name in Jenkins (Global Tool Config)
        maven 'Maven 3.9.6'      // ✅ Exactly match Maven name in Jenkins
    }

    environment {
        SONARQUBE_SERVER = 'MySonarQube' // ✅ Replace with the exact SonarQube server name in Jenkins
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
