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
                configFileProvider([configFile(fileId: 'Przemo179v1', variable: 'SETTINGS_XML')]) {
                    bat "mvn clean install --settings %SETTINGS_XML%"
                }
            }
        }
        stage('Deploy') {
            steps {
                configFileProvider([configFile(fileId: 'Przemo179v1', variable: 'SETTINGS_XML')]) {
                    bat "mvn deploy --settings %SETTINGS_XML%"
                }
            }
        }
    }
}