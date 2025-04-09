pipeline {
    agent any

    tools {
        maven 'maven 3.9.9'
        jdk 'jdk21'
    }

    environment {
        // Set JAVA_HOME and MAVEN_HOME globally
        JAVA_HOME = tool name: 'jdk21', type: 'hudson.model.JDK'
        MAVEN_HOME = tool name: 'maven_3.9.9', type: 'hudson.tasks.Maven_MavenInstallation'
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Przemo179/firstmavenapp'
            }
        }

        stage('Build') {
            steps {
                bat 'echo JAVA_HOME=%JAVA_HOME%'
                bat 'java -version'
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
