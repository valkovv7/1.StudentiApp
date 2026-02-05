pipeline {
    agent any
    stages {
        stage('Test Docker') {
            steps {
                sh 'docker version'
            }
        }
    }
}


// pipeline {
//     agent {
//         docker {
//             image 'node:18'
//             args '-u root'
//         }
//     }

//     stages {
//         stage('Checkout') {
//             steps {
//                 checkout scm
//             }
//         }

//         stage('Install dependencies') {
//             steps {
//                 sh 'npm install'
//             }
//         }

//         stage('Run tests') {
//             steps {
//                 sh 'npm test'
//             }
//         }
//     }
// }
