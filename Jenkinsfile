pipeline {
    agent any

    tools {
        maven 'Maven 3.9.6'        // Change this if your Maven version name is different in Jenkins
        jdk 'JDK 17'               // Change this if your JDK version name is different
    }

    environment {
        SONAR_SCANNER_HOME = tool 'SonarQube Scanner'  // Must match the name set in Jenkins tools
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/dharshini-devops23/devops-practice.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonarQube') {
                    sh '''
                        ${SONAR_SCANNER_HOME}/bin/sonar-scanner \
                        -Dsonar.projectKey=devops-practice \
                        -Dsonar.sources=. \
                        -Dsonar.java.binaries=target
                    '''
                }
            }
        }
    }
}
