pipeline {
    agent any
    stages {
        stage('Non-Parallel Stage') {
            steps {
                echo 'This stage will be executed first.'
            }
        }
        stage('Parallel Stage') {
            failFast true
            parallel {
                stage('sub-stage A') {
                    agent any
                    steps {
                        echo "On sub-stage A"
                        sleep 5
                    }
                }
                stage('sub-stage B') {
                    agent any
                    steps {
                        echo "On sub-stage B"
                        sleep 10
                    }
                }
                stage('sub-stage C') {
                    agent any
                    stages {
                        stage('Nested stage-1') {
                            steps {
                                echo "In stage Nested stage-1 within sub-stage C"
                                sleep 10
                            }
                        }
                        stage('Nested stage-2') {
                            steps {
                                echo "In stage Nested stage-2 within sub-stage C"
                                sleep 10
                            }
                        }
                    }
                }
            }
        }
    }
}
