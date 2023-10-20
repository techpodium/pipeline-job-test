pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sshagent(credentials: ['jenkins-user-ssh-private-key']) {
                  sh ("scp web/* root@192.168.56.3:/var/www/html/")
                }
            }
        }
    }
}
