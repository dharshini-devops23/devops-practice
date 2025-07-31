pipeline {
    agent any

    tools {
        jdk 'JDK 17'
        maven 'Maven 3.9.6'
    }

    environment {
        SONARQUBE_ENV = 'MySonar'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_ENV}") {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
