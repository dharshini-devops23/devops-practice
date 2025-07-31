pipeline {
    agent any

    tools {
        hudson.plugins.sonar.SonarRunnerInstallation 'SonarScanner'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/dharshini-devops23/devops-practice.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonarQube') {
                    sh 'sonar-scanner'
                }
            }
        }
    }
}
