pipeline {
    agent any
    stages {
        stage('Info') {
            steps {
                echo "Job: ${JOB_NAME} is building on branch ${BRANCH_NAME} and build-id is ${BUILD_ID}"
                sh 'sleep 5'
            }
        }
        stage('Build') {
            steps {
                echo "this is build stage"
                sh 'sleep 5'
            }
        }
        stage('Test') {
            steps {
                echo "this is test stage"
                sh 'sleep 5'
            }
        }
        stage('Deploy') {
            steps {
                echo "this is deploy stage"
                sh 'sleep 5'
            }
        }
    }
}
