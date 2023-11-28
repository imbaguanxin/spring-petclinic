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
                sh 'sleep 2'
                // sh 'ansible-playbook playbook.yml -i inventory.ini -b --become-user vagrant'         
            }
        }
    }
}