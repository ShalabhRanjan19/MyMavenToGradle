pipeline {
    agent any

    tools {
        jdk 'jdk-17'         // Ensure 'jdk-17' is configured in Jenkins > Global Tool Configuration
        gradle 'Gradle'      // Ensure 'Gradle' is configured similarly
    }

    environment {
        JAVA_HOME = "${tool 'jdk-17'}"
        GRADLE_HOME = "${tool 'Gradle'}"
        PATH = "${JAVA_HOME}/bin:${GRADLE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ShalabhRanjan19/MyMavenToGradle.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'gradle clean build'
            }
        }

        stage('Test') {
            steps {
                sh 'gradle test'
            }
        }

        stage('Archive JAR') {
            steps {
                sh 'java -jar build/libs/MyMavenToGradle-1.0-SNAPSHOT.jar'

            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
