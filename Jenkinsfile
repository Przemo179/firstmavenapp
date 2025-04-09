pipeline {
    agent any

    tools {
        maven 'maven 3.9.9'
        jdk 'jdk21'
    }

    stages {
        stage('Setup JAVA_HOME') {
            steps {
                script {
                    def rawHome = tool name: 'jdk21', type: 'hudson.model.JDK'
                    env.JAVA_HOME = "${rawHome}\\jdk-21.0.6"
                    env.PATH = "${env.JAVA_HOME}\\bin;${env.PATH}"
                }
            }
        }
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
                bat 'mvn -version'
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
