pipeline {
    agent any

    stages {
        stage('Cleanup') {
            steps {
                cleanWs()
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'find ./ -name "*.js" -print0 | xargs -0 jslint > jslint.html || true'
                archiveArtifacts artifacts: 'jslint.html', followSymlinks: false
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'zip -r artifact.zip . -x ".git/*" -x jslint.html'
                archiveArtifacts artifacts: 'artifact.zip', followSymlinks: false
            }
        }
        stage('Deploy') {
            steps {
                sshagent(['ssh-key']) {
                    sh 'pwd'
                    sh 'scp -o StrictHostKeyChecking=no artifact.zip root@3.96.152.145:/var/www/html/'
                    sh 'ssh -tt root@3.96.152.145 -o StrictHostKeyChecking=no "cd /var/www/html/; unzip -o artifact.zip; rm artifact.zip"'
                }
            }
        }
    }
}
