pipeline {
    agent any

    tools {
        jdk 'jdk-17'          // Must be defined in Jenkins Global Tool Config
        gradle 'Gradle' 
        mavem 'maven-3.9.0'
        // Same here; name must match Jenkins config
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ShalabhRanjan19/MyMavenToGradle.git'
            }
        }

        stage('Build') {
            steps {
                sh './gradle clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradle test'
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }
}
