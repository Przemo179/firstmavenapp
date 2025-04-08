pipeline {
    agent any

    tools {
        maven 'maven_3.9.9'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Przemo179/firstmavenapp'
            }
        }

        stage('Build') {
            steps {
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
