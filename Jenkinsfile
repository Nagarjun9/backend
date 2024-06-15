
pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }

    environment {
            def appVersion =  ''
    }
    stages {
        // stage('test'){
        //     steps{
        //         script{
        //             sh """
        //             echo "this is testing" 
        //             ls -l
        //             """
        //         }
        //     }
        
        // }

         stage('read the version'){
            steps {
                script{
                def packageJson = readJSON file: 'package.json'
                appVersion = packageJson.version
                echo "applocation version: $appVersion"
                }
            }
         }
          stage('Install Dependencies'){
              steps{
                sh """
                npm install 
                ls -ltr
                echo "applocation version: $appVersion"
                """
              }
          }
       
    }
     post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'I will run when pipeline is success'
        }
        failure { 
            echo 'I will run when pipeline is failure'
        }
    }
}


// pipeline {
//     agent {
//         label 'AGENT-1'
//     }
//     options {
//         timeout(time: 30, unit: 'MINUTES')
//         disableConcurrentBuilds()
//         ansiColor('xterm')
//     }
//     environment{
//         def appVersion = '' //variable declaration
//     }
//     stages {
//         stage('read the version'){
//             steps{
//                 script{
//                     def packageJson = readJSON file: 'package.json'
//                     appVersion = packageJson.version
//                     echo "application version: $appVersion"
//                 }
//             }
//         }
//         stage('Install Dependencies') {
//             steps {
//                sh """
//                 npm install
//                 ls -ltr
//                 echo "application version: $appVersion"
//                """
//             }
//         }
//         // stage('Build'){
//         //     steps{
//         //         sh """
//         //         zip -q -r backend-${appVersion}.zip * -x Jenkinsfile -x backend-${appVersion}.zip
//         //         ls -ltr
//         //         """
//         //     }
//         // }
//     }
//     post { 
//         always { 
//             echo 'I will always say Hello again!'
//             deleteDir()
//         }
//         success { 
//             echo 'I will run when pipeline is success'
//         }
//         failure { 
//             echo 'I will run when pipeline is failure'
//         }
//     }
// }