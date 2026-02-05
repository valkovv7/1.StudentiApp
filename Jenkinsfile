// pipeline {
//     agent any
//     stages {
//         stage('Docker Check') {
//             steps {
//                 sh 'whoami'
//                 sh 'docker ps'
//             }
//         }
//     }
// }

/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent {
        docker {
            image 'node:18'
            args '-u root'
        }
    }

   environment {
        RENDER_API_KEY = credentials('RENDER_API_KEY')
        RENDER_SERVICE_ID = credentials('RENDER_SERVICE_ID')
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
        
        stage('Deploy') {
            steps {
                // Call Render API using curl
                sh """
                curl -X POST https://api.render.com/deploy/${RENDER_SERVICE_ID} \\
                  -H 'Accept: application/json' \\
                  -H 'Authorization: Bearer ${RENDER_API_KEY}'
                """
            }
        }
    }
}
