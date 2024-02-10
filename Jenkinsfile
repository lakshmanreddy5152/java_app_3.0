pipeline {
    agent any

   // tools {
        // Install the Maven version configured as "M3" and add it to the path.
       // maven "M3"
   // }

    stages {
        stage('Git checkout') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', credentialsId: 'git credentials', url: 'https://github.com/lakshmanreddy5152/java_app_3.0.git'

            }
        }

        stage('Maven build') {
            steps {
                sh "mvn clean install"
            }
        }  
    }
}
