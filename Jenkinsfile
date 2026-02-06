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

        // stage('Deploy') {
        //     when {
        //         branch 'main'
        //     }
        //     steps {
        //         withCredentials([
        //             string(credentialsId: 'RENDER_API_KEY', variable: 'API_KEY'),
        //             string(credentialsId: 'RENDER_SERVICE_ID', variable: 'SERVICE_ID')
        //         ]) {

        //         sh ' curl -X POST https://api.render.com/deploy/${SERVICE_ID} \
        //             -H "Accept: application/json" \
        //             -H "Authorization: Bearer ${API_KEY}"'
        //         }
        //     }
        // }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                withCredentials([
            string(credentialsId: 'RENDER_API_KEY', variable: 'RENDER_API_KEY'),
            string(credentialsId: 'RENDER_SERVICE_ID', variable: 'RENDER_SERVICE_ID')
        ]) {
                    sh '''
            curl -X POST "https://api.render.com/deploy/$RENDER_SERVICE_ID" \
              -H "Accept: application/json" \
              -H "Authorization: Bearer $RENDER_API_KEY"
            '''
        }
            }
        }
    }
}
