pipeline {
    agent any

    tools {
        jdk 'jdk11'          // Must be defined in Jenkins Global Tool Config
        gradle 'gradle7'     // Same here; name must match Jenkins config
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ShalabhRanjan19/MyMavenToGradle.git'
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
}
