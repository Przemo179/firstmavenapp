pipeline {
    agent any
    environment {
        MAVEN_SETTINGS = credentials('Przemo179v1') // this is your Secret File ID
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Przemo179/firstmavenapp.git'
            }
        }
        stage('Build') {
            steps {
                configFileProvider([configFile(fileId: 'Przemo179', variable: 'SETTINGS_XML')]) {
                    bat "mvn clean install --settings %SETTINGS_XML%"
                }
            }
        }
        stage('Deploy') {
            steps {
                configFileProvider([configFile(fileId: 'Przemo179', variable: 'SETTINGS_XML')]) {
                    bat "mvn deploy --settings %SETTINGS_XML%"
                }
            }
        }
    }
}