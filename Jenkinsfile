pipeline {
    agent {
        docker {
            image 'maven:3-eclipse-temurin-17'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {

        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests -Dmaven.wagon.http.ssl.insecure=true clean package'
            }
        }
        // stage('SonarQube analysis') {
        //     steps {
        //         withSonarQubeEnv('sonarqube-container') {
        //         sh 'mvn sonar:sonar'
        //         }
        //     }
        // }
        stage('Run') {
            steps {
                sh 'java -Dserver.port=8081 -jar target/spring-petclinic-3.1.0-SNAPSHOT.jar'
            }
        }
    }
}