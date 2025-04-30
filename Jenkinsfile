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
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            junit 'build/test-results/test/*.xml'
            cleanWs()
        }
    }
}
