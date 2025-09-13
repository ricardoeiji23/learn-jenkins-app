pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci 
                    npm run build 
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage'
            }
        }

    }
}


// ----------------------------------------------
// pipeline {
//     agent any

//     environment {
//         NETLIFY_SITE_ID = 'af71623f-489d-4acc-accd-d48672d4dcf8' 
//         NETLIFY_AUTH_TOKEN = credentials('netlify-token')
//     }

//     stages {

//         stage('Build') {
//             agent {
//                 docker {
//                     image 'node:18-alpine'
//                     reuseNode true
//                 }
//             }   
//             steps {
//                 sh '''
//                     ls -la
//                     node --version
//                     npm --version
//                     npm ci
//                     npm run build
//                     ls -la
//                 '''
//             }
//         }

//         stage('Test') {
//             agent {
//                 docker {
//                     image 'node:18-alpine'
//                     reuseNode true
//                 }
//             }

//             steps {
//                 sh '''
//                     echo "running tests..."
//                     npm ci
//                     npm test 
//                 '''
//             }
            
//             post {
//                 always {
//                     junit '**/junit.xml'
//                 }
//             }

//         // --------------------------------
//            /* parallel { // This is from his video and I couldn't see all
//                 stage('Unit tests') {
//                     agent {
//                         docker {
//                             image 'node:18-alpine'
//                             reuseNode true
//                         }
//                     }

//                     steps {
//                         sh '''
//                             #test -f build/index.html
//                             npm test
//                         '''
//                     }
//                     post {
//                         always {
//                             junit 'jest-results/junit.xml'
//                         }
//                     }
//                 }

//                 stage('E2E') {
//                     agent {
//                         docker {
//                             image 'mcr.microsoft.com/playwright:v1.39.0-jammy'
//                             reuseNode true
//                         }
//                     }

//                     steps {
//                         sh '''
//                             npm install serve
//                             node_modules/.bin/serve -s build &
//                             sleep 10
//                             npx playwright test --reporter=html 
//                         '''
//                     }

//                     post {
//                         always{
//                             publishHTML([allowMissing:false, alwaysLinktoLastBuild: false, keepAll: false, reportDir: 'p'])
//                         }
//                     }

//                 }

//             }*/

//             // -------------------------------------
//             /*agent { // This is ok
//                 docker {
//                     image 'node:18-alpine'
//                     reuseNode true
//                 }
//             }

    
//             steps {
//                 sh '''
//                     test -f build/index.html 
//                     npm test 
//                 '''
//             }*/
//         }

//         stage('Deploy') {
//             agent {
//                 docker {
//                     image 'node:18'
//                     reuseNode true
//                 }
//             }

//             steps {
//                 sh '''
//                     npm install netlify-cli
//                     node_modules/.bin/netlify --version
//                     echo "Deploying to production. Site ID: $NETLIFY_SITE_ID"
//                     node_modules/.bin/netlify status
//                     node_modules/.bin/netlify deploy --dir=Portfolio-code --prod
//                 '''
//             }
//         }


//     }


// }
