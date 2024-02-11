pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven"
    }

    stages {
        stage('Git checkout') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', credentialsId: 'git credentials', url: 'https://github.com/lakshmanreddy5152/java_app_3.0.git'

            }
        }

        stage('Unit Test Maven') {
            steps {
                sh 'mvn test'
            }
        }  

        stage('Integration Test Maven') {
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }  

        stage('Static code analysys Sonarqube') {
            steps {
                withSonarQubeEnv('sonar-api') {
                    sh 'mvn clean package sonar:sonar'
                      }
            }
        }  

        stage('Quality gate status check sonar') {
            steps {
                waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api'
            }
        }  

        stage('Maven build') {
            steps {
                sh "mvn clean install"
            }
        }  
    }
}
