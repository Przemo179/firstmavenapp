pipeline {
    agent any

    tools {
        maven 'maven 3.9.9'  // The Maven installation you have configured in Jenkins
        jdk 'jdk21'          // The JDK installation you have configured in Jenkins
    }

    environment {
        // Set JAVA_HOME and MAVEN_HOME globally
        JAVA_HOME = tool name: 'jdk21', type: 'hudson.model.JDK'
        MAVEN_HOME = tool name: 'maven 3.9.9', type: 'hudson.tasks.Maven_MavenInstallation'
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub repository
                git 'https://github.com/Przemo179/firstmavenapp'
            }
        }

        stage('Build') {
            steps {
                // Display JAVA_HOME and check if Java is set correctly
                bat 'echo JAVA_HOME=%JAVA_HOME%'
                
                // Display Java version to ensure the right JDK is being used
                bat 'java -version'
                
                // Run Maven build (clean and package)
                bat 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                // Run Maven deploy with debug information
                bat 'mvn deploy -X'
            }
        }
    }

    post {
        always {
            // Clean up actions, if necessary (e.g., deleting temporary files, etc.)
            echo 'Cleaning up after the build.'
        }
        success {
            // Actions to take if the build was successful
            echo 'Build and deployment were successful!'
        }
        failure {
            // Actions to take if the build failed
            echo 'Build or deployment failed.'
        }
    }
}
