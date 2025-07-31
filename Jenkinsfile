pipeline {
    agent any

    tools {
        jdk 'JDK 17'               // Exactly match the name from Global Tool Config
        maven 'Maven_3.9.6'        // Exactly match the name from Global Tool Config
    }

    environment {
        SONARQUBE_ENV = 'MySonar'  // Must match your SonarQube installation name
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
