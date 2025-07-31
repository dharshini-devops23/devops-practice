pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/dharshini-devops23/devops-practice.git', branch: 'main'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonarQube') {
                    bat 'sonar-scanner -Dsonar.projectKey=devops-practice -Dsonar.sources=.'
                }
            }
        }
    }
}
