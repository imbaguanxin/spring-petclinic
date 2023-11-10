pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage("SonarQube analysis") {
            steps {
                withSonarQubeEnv('sonarqube-container') {
                sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}