pipeline {
    agent any
    stages {
        stage('Docker Check') {
            steps {
                sh 'whoami'
                sh 'docker ps'
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
