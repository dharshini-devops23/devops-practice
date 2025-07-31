pipeline {
    agent any

    tools {
        sonarQubeScanner 'SonarScanner'  // 🟡 Exactly match the tool name in Jenkins config
        jdk 'JDK 17'                     // ✅ Your configured JDK
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/dharshini-devops23/devops-practice.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonarQube') {  // 🟢 Name should match SonarQube server name in Jenkins
                    sh '''
                        sonar-scanner \
                        -Dsonar.projectKey=devops-practice \
                        -Dsonar.sources=. \
                        -Dsonar.projectName=devops-practice \
                        -Dsonar.host.url=http://localhost:9000
                    '''
                }
            }
        }
    }
}
