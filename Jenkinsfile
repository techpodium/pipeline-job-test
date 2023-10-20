pipeline {
    agent any
    options {
        // This is required if you want to clean before build
        skipDefaultCheckout(true)
    }
    stages {
        stage('Build') {
            steps {
                cleanWs()
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
