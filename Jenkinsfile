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
                    // Renaming the settings.xml.txt to settings.xml for Maven
                    bat 'copy %SETTINGS_XML% %WORKSPACE%\\settings.xml' // Windows
                    bat "mvn clean install --settings %WORKSPACE%\\settings.xml"
                }
            }
        }
        stage('Deploy') {
            steps {
                configFileProvider([configFile(fileId: 'Przemo179v1', variable: 'SETTINGS_XML')]) {
                    // Renaming the settings.xml.txt to settings.xml for Maven
                    bat 'copy %SETTINGS_XML% %WORKSPACE%\\settings.xml' // Windows
                    bat "mvn deploy --settings %WORKSPACE%\\settings.xml"
                }
            }
        }
    }
}