pipeline {
    agent none

    stages {
        stage('Build and Test') {
            matrix {
                axes {
                    axis {
                        name 'NODE_VERSION'
                        values '18', '20', '22'
                    }
                }

                agent {
                    docker {
                        image "node:${NODE_VERSION}"
                        args '-u root'
                    }
                }

                stages {
                    stage('Checkout') {
                        steps {
                            checkout scm
                        }
                    }

                    stage('Install dependencies') {
                        steps {
                            sh 'npm install'
                        }
                    }

                    stage('Run tests') {
                        steps {
                            sh 'npm test'
                        }
                    }
                }
            }
        }
    }
}
