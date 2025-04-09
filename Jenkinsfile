pipeline {
    agent any

    tools {
        maven 'maven 3.9.9'
        jdk 'jdk21'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Przemo179/firstmavenapp'
            }
        }

        stage('Build') {
            steps {
                // Print JAVA_HOME and PATH set by Jenkins
                bat 'echo JAVA_HOME=%JAVA_HOME%'  // Print JAVA_HOME to verify JDK is correctly set
                bat 'echo PATH=%PATH%'  // Print PATH to verify Java and Maven are correctly added
                bat 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                bat 'mvn deploy -X'
            }
        }
    }
}
