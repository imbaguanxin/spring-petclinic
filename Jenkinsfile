pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building.."'
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('Ansible') {
            steps {
                sh 'echo "Copying artifact to webserver.."'
                ansiblePlaybook(
                    playbook: 'playbook.yml',
                )            
            }
        }
    }
}