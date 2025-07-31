pipeline {
    agent any

    tools {
        maven 'Maven 3.8.8'      // Your configured Maven version name
    }

    stages {
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonar') {
                    sh 'mvn clean verify sonar:sonar'
                }
            }
        }
    }
}
