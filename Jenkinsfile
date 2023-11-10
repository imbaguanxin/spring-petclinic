pipeline {
    agent {
        docker {
            image 'maven:3.9.5-eclipse-temurin-17-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {

        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        // stage('SonarQube analysis') {
        //     steps {
        //         withSonarQubeEnv('sonarqube-container') {
        //         sh 'mvn sonar:sonar'
        //         }
        //     }
        // }
        stage('Publish') {
            steps {
                sh 'mvnw package'
            }
            post {
                success {
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}