pipeline {
    agent any

    tools {
        maven 'maven 3.9.9'
        jdk 'jdk21'
    }

    stages {
          steps {
                script {
                    // Dynamically resolve the correct JDK path
                    def baseJdkPath = tool name: 'jdk21', type: 'hudson.model.JDK'
                    def jdkSubdir = new File(baseJdkPath).listFiles().find {
                        it.isDirectory() && it.name.toLowerCase().startsWith("jdk")
                    }
                    def resolvedJdkPath = jdkSubdir != null ? jdkSubdir.absolutePath : baseJdkPath

                    // Dynamically resolve the correct Maven path
                    def baseMavenPath = tool name: 'maven_3.9.9', type: 'hudson.tasks.Maven_MavenInstallation'

                    // Set JAVA_HOME and MAVEN_HOME
                    env.JAVA_HOME = resolvedJdkPath
                    env.MAVEN_HOME = baseMavenPath
                    env.PATH = "${env.JAVA_HOME}\\bin;${env.MAVEN_HOME}\\bin;${env.PATH}"

                    echo "Resolved JAVA_HOME: ${env.JAVA_HOME}"
                    echo "Resolved MAVEN_HOME: ${env.MAVEN_HOME}"
                }
            }

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
