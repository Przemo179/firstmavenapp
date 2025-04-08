pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Przemo179/firstmavenapp.git'
            }
        }

        stage('Build') {
            steps {
                // Use 'sh' for Linux/macOS or 'bat' for Windows
                bat 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                bat 'mvn deploy'
            }
        }
    }
}
